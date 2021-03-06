
---
title: "EventTarget"
block_external_search_index: true
---



Provides a CloudWatch Event Target resource.

{{% examples %}}
## Example Usage
{{% example %}}

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const console = new aws.cloudwatch.EventRule("console", {
    description: "Capture all EC2 scaling events",
    eventPattern: `{
  "source": [
    "aws.autoscaling"
  ],
  "detail-type": [
    "EC2 Instance Launch Successful",
    "EC2 Instance Terminate Successful",
    "EC2 Instance Launch Unsuccessful",
    "EC2 Instance Terminate Unsuccessful"
  ]
}
`,
});
const testStream = new aws.kinesis.Stream("test_stream", {
    shardCount: 1,
});
const yada = new aws.cloudwatch.EventTarget("yada", {
    arn: testStream.arn,
    rule: console.name,
    runCommandTargets: [
        {
            key: "tag:Name",
            values: ["FooBar"],
        },
        {
            key: "InstanceIds",
            values: ["i-162058cd308bffec2"],
        },
    ],
});
```

{{% /example %}}
{{% /examples %}}
## Example SSM Document Usage

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const ssmLifecycleTrust = aws.iam.getPolicyDocument({
    statements: [{
        actions: ["sts:AssumeRole"],
        principals: [{
            identifiers: ["events.amazonaws.com"],
            type: "Service",
        }],
    }],
});
const stopInstance = new aws.ssm.Document("stop_instance", {
    content: `  {
    "schemaVersion": "1.2",
    "description": "Stop an instance",
    "parameters": {

    },
    "runtimeConfig": {
      "aws:runShellScript": {
        "properties": [
          {
            "id": "0.aws:runShellScript",
            "runCommand": ["halt"]
          }
        ]
      }
    }
  }
`,
    documentType: "Command",
});
const ssmLifecyclePolicyDocument = stopInstance.arn.apply(arn => aws.iam.getPolicyDocument({
    statements: [
        {
            actions: ["ssm:SendCommand"],
            conditions: [{
                test: "StringEquals",
                values: ["*"],
                variable: "ec2:ResourceTag/Terminate",
            }],
            effect: "Allow",
            resources: ["arn:aws:ec2:eu-west-1:1234567890:instance/*"],
        },
        {
            actions: ["ssm:SendCommand"],
            effect: "Allow",
            resources: [arn],
        },
    ],
}));
const ssmLifecycleRole = new aws.iam.Role("ssm_lifecycle", {
    assumeRolePolicy: ssmLifecycleTrust.json,
});
const ssmLifecyclePolicy = new aws.iam.Policy("ssm_lifecycle", {
    policy: ssmLifecyclePolicyDocument.json,
});
const stopInstancesEventRule = new aws.cloudwatch.EventRule("stop_instances", {
    description: "Stop instances nightly",
    scheduleExpression: "cron(0 0 * * ? *)",
});
const stopInstancesEventTarget = new aws.cloudwatch.EventTarget("stop_instances", {
    arn: stopInstance.arn,
    roleArn: ssmLifecycleRole.arn,
    rule: stopInstancesEventRule.name,
    runCommandTargets: [{
        key: "tag:Terminate",
        values: ["midnight"],
    }],
});
```

## Example RunCommand Usage

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const stopInstancesEventRule = new aws.cloudwatch.EventRule("stop_instances", {
    description: "Stop instances nightly",
    scheduleExpression: "cron(0 0 * * ? *)",
});
const stopInstancesEventTarget = new aws.cloudwatch.EventTarget("stop_instances", {
    arn: `arn:aws:ssm:${var_aws_region}::document/AWS-RunShellScript`,
    input: "{\"commands\":[\"halt\"]}",
    roleArn: aws_iam_role_ssm_lifecycle.arn,
    rule: stopInstancesEventRule.name,
    runCommandTargets: [{
        key: "tag:Terminate",
        values: ["midnight"],
    }],
});
```

## Example ECS Run Task with Role and Task Override Usage

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const ecsEvents = new aws.iam.Role("ecs_events", {
    assumeRolePolicy: `{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "",
      "Effect": "Allow",
      "Principal": {
        "Service": "events.amazonaws.com"
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
`,
});
const ecsEventsRunTaskWithAnyRole = new aws.iam.RolePolicy("ecs_events_run_task_with_any_role", {
    policy: aws_ecs_task_definition_task_name.arn.apply(arn => `{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "iam:PassRole",
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": "ecs:RunTask",
            "Resource": "${arn.replace(/:\d+$/, ":*")}"
        }
    ]
}
`),
    role: ecsEvents.id,
});
const ecsScheduledTask = new aws.cloudwatch.EventTarget("ecs_scheduled_task", {
    arn: aws_ecs_cluster_cluster_name.arn,
    ecsTarget: {
        taskCount: 1,
        taskDefinitionArn: aws_ecs_task_definition_task_name.arn,
    },
    input: `{
  "containerOverrides": [
    {
      "name": "name-of-container-to-override",
      "command": ["bin/console", "scheduled-task"]
    }
  ]
}
`,
    roleArn: ecsEvents.arn,
    rule: aws_cloudwatch_event_rule_every_hour.name,
});
```



## Create a EventTarget Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/cloudwatch/#EventTarget">EventTarget</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/cloudwatch/#EventTargetArgs">EventTargetArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">EventTarget</span><span class="p">(resource_name, opts=None, </span>arn=None<span class="p">, </span>batch_target=None<span class="p">, </span>ecs_target=None<span class="p">, </span>input=None<span class="p">, </span>input_path=None<span class="p">, </span>input_transformer=None<span class="p">, </span>kinesis_target=None<span class="p">, </span>role_arn=None<span class="p">, </span>rule=None<span class="p">, </span>run_command_targets=None<span class="p">, </span>sqs_target=None<span class="p">, </span>target_id=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewEventTarget<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v2/go/pulumi?tab=doc#Context">Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/cloudwatch?tab=doc#EventTargetArgs">EventTargetArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v2/go/pulumi?tab=doc#ResourceOption">ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/cloudwatch?tab=doc#EventTarget">EventTarget</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.CloudWatch.EventTarget.html">EventTarget</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.CloudWatch.EventTargetArgs.html">EventTargetArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language nodejs %}}

<dl class="resources-properties">
    <dt class="property-required" title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The unique name of the resource.</dd>
    <dt class="property-optional" title="Optional">
        <span>args</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The arguments to use to populate this resource's properties.</dd>
    <dt class="property-optional" title="Optional">
        <span>opts</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>A bag of options that control this resource's behavior.</dd>
</dl>

{{% /choosable %}}

{{% choosable language python %}}
<dl class="resources-properties">
    <dt class="property-required" title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The unique name of the resource.</dd>
    <dt class="property-optional" title="Optional">
        <span>opts</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>A bag of options that control this resource's behavior.</dd>
</dl>
{{% /choosable %}}

{{% choosable language go %}}

<dl class="resources-properties">
    <dt class="property-required" title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The unique name of the resource.</dd>
    <dt class="property-optional" title="Optional">
        <span>args</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The arguments to use to populate this resource's properties.</dd>
    <dt class="property-optional" title="Optional">
        <span>opts</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>A bag of options that control this resource's behavior.</dd>
</dl>

{{% /choosable %}}

{{% choosable language csharp %}}

<dl class="resources-properties">
    <dt class="property-required" title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The unique name of the resource.</dd>
    <dt class="property-optional" title="Optional">
        <span>args</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The arguments to use to populate this resource's properties.</dd>
    <dt class="property-optional" title="Optional">
        <span>opts</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>A bag of options that control this resource's behavior.</dd>
</dl>

{{% /choosable %}}

#### Resource Arguments




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The Amazon Resource Name (ARN) associated of the target.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Rule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The name of the rule you want to add targets to.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Batch<wbr>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetbatchtarget">Event<wbr>Target<wbr>Batch<wbr>Target<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke an Amazon Batch Job. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ecs<wbr>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetecstarget">Event<wbr>Target<wbr>Ecs<wbr>Target<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke Amazon ECS Task. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Input</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}Valid JSON text passed to the target.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Input<wbr>Path</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The value of the [JSONPath](http://goessner.net/articles/JsonPath/)
that is used for extracting part of the matched event when passing it to the target.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Input<wbr>Transformer</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetinputtransformer">Event<wbr>Target<wbr>Input<wbr>Transformer<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are providing a custom input to a target based on certain event data.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Kinesis<wbr>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetkinesistarget">Event<wbr>Target<wbr>Kinesis<wbr>Target<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke an Amazon Kinesis Stream. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The Amazon Resource Name (ARN) of the IAM role to be used for this target when the rule is triggered. Required if `ecs_target` is used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Run<wbr>Command<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetruncommandtarget">List&lt;Event<wbr>Target<wbr>Run<wbr>Command<wbr>Target<wbr>Args&gt;</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke Amazon EC2 Run Command. Documented below. A maximum of 5 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sqs<wbr>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetsqstarget">Event<wbr>Target<wbr>Sqs<wbr>Target<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke an Amazon SQS Queue. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Target<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The unique target assignment ID.  If missing, will generate a random, unique id.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The Amazon Resource Name (ARN) associated of the target.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Rule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The name of the rule you want to add targets to.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Batch<wbr>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetbatchtarget">Event<wbr>Target<wbr>Batch<wbr>Target</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke an Amazon Batch Job. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ecs<wbr>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetecstarget">Event<wbr>Target<wbr>Ecs<wbr>Target</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke Amazon ECS Task. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Input</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}Valid JSON text passed to the target.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Input<wbr>Path</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The value of the [JSONPath](http://goessner.net/articles/JsonPath/)
that is used for extracting part of the matched event when passing it to the target.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Input<wbr>Transformer</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetinputtransformer">Event<wbr>Target<wbr>Input<wbr>Transformer</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are providing a custom input to a target based on certain event data.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Kinesis<wbr>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetkinesistarget">Event<wbr>Target<wbr>Kinesis<wbr>Target</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke an Amazon Kinesis Stream. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The Amazon Resource Name (ARN) of the IAM role to be used for this target when the rule is triggered. Required if `ecs_target` is used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Run<wbr>Command<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetruncommandtarget">[]Event<wbr>Target<wbr>Run<wbr>Command<wbr>Target</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke Amazon EC2 Run Command. Documented below. A maximum of 5 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sqs<wbr>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetsqstarget">Event<wbr>Target<wbr>Sqs<wbr>Target</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke an Amazon SQS Queue. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Target<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The unique target assignment ID.  If missing, will generate a random, unique id.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The Amazon Resource Name (ARN) associated of the target.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>rule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The name of the rule you want to add targets to.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>batch<wbr>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetbatchtarget">Event<wbr>Target<wbr>Batch<wbr>Target</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke an Amazon Batch Job. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ecs<wbr>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetecstarget">Event<wbr>Target<wbr>Ecs<wbr>Target</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke Amazon ECS Task. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>input</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}Valid JSON text passed to the target.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>input<wbr>Path</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The value of the [JSONPath](http://goessner.net/articles/JsonPath/)
that is used for extracting part of the matched event when passing it to the target.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>input<wbr>Transformer</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetinputtransformer">Event<wbr>Target<wbr>Input<wbr>Transformer</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are providing a custom input to a target based on certain event data.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>kinesis<wbr>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetkinesistarget">Event<wbr>Target<wbr>Kinesis<wbr>Target</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke an Amazon Kinesis Stream. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The Amazon Resource Name (ARN) of the IAM role to be used for this target when the rule is triggered. Required if `ecs_target` is used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>run<wbr>Command<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetruncommandtarget">Event<wbr>Target<wbr>Run<wbr>Command<wbr>Target[]</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke Amazon EC2 Run Command. Documented below. A maximum of 5 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sqs<wbr>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetsqstarget">Event<wbr>Target<wbr>Sqs<wbr>Target</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke an Amazon SQS Queue. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>target<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The unique target assignment ID.  If missing, will generate a random, unique id.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The Amazon Resource Name (ARN) associated of the target.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>rule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The name of the rule you want to add targets to.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>batch_<wbr>target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetbatchtarget">Dict[Event<wbr>Target<wbr>Batch<wbr>Target]</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke an Amazon Batch Job. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ecs_<wbr>target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetecstarget">Dict[Event<wbr>Target<wbr>Ecs<wbr>Target]</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke Amazon ECS Task. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>input</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}Valid JSON text passed to the target.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>input_<wbr>path</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The value of the [JSONPath](http://goessner.net/articles/JsonPath/)
that is used for extracting part of the matched event when passing it to the target.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>input_<wbr>transformer</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetinputtransformer">Dict[Event<wbr>Target<wbr>Input<wbr>Transformer]</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are providing a custom input to a target based on certain event data.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>kinesis_<wbr>target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetkinesistarget">Dict[Event<wbr>Target<wbr>Kinesis<wbr>Target]</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke an Amazon Kinesis Stream. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>role_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The Amazon Resource Name (ARN) of the IAM role to be used for this target when the rule is triggered. Required if `ecs_target` is used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>run_<wbr>command_<wbr>targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetruncommandtarget">List[Event<wbr>Target<wbr>Run<wbr>Command<wbr>Target]</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke Amazon EC2 Run Command. Documented below. A maximum of 5 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sqs_<wbr>target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetsqstarget">Dict[Event<wbr>Target<wbr>Sqs<wbr>Target]</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke an Amazon SQS Queue. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>target_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The unique target assignment ID.  If missing, will generate a random, unique id.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}










## Look up an Existing EventTarget Resource

Get an existing EventTarget resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">Input&lt;ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/cloudwatch/#EventTargetState">EventTargetState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/cloudwatch/#EventTarget">EventTarget</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>arn=None<span class="p">, </span>batch_target=None<span class="p">, </span>ecs_target=None<span class="p">, </span>input=None<span class="p">, </span>input_path=None<span class="p">, </span>input_transformer=None<span class="p">, </span>kinesis_target=None<span class="p">, </span>role_arn=None<span class="p">, </span>rule=None<span class="p">, </span>run_command_targets=None<span class="p">, </span>sqs_target=None<span class="p">, </span>target_id=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetEventTarget<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v2/go/pulumi?tab=doc#Context">Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v2/go/pulumi?tab=doc#IDInput">IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/cloudwatch?tab=doc#EventTargetState">EventTargetState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v2/go/pulumi?tab=doc#ResourceOption">ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/cloudwatch?tab=doc#EventTarget">EventTarget</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.CloudWatch.EventTarget.html">EventTarget</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.CloudWatch.EventTargetState.html">EventTargetState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language nodejs %}}

<dl class="resources-properties">
    <dt class="property-required" title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The unique name of the resulting resource.</dd>
    <dt class="property-required" title="Required">
        <span>id</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The <em>unique</em> provider ID of the resource to lookup.</dd>
    <dt class="property-optional" title="Optional">
        <span>state</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>Any extra arguments used during the lookup.</dd>
    <dt class="property-optional" title="Optional">
        <span>opts</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>A bag of options that control this resource's behavior.</dd>
</dl>

{{% /choosable %}}

{{% choosable language python %}}
<dl class="resources-properties">
    <dt class="property-required" title="Required">
        <span>resource_name</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The unique name of the resulting resource.</dd>
    <dt class="property-required" title="Optional">
        <span>id</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The <em>unique</em> provider ID of the resource to lookup.</dd>
</dl>
{{% /choosable %}}

{{% choosable language go %}}

<dl class="resources-properties">
    <dt class="property-required" title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The unique name of the resulting resource.</dd>
    <dt class="property-required" title="Required">
        <span>id</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The <em>unique</em> provider ID of the resource to lookup.</dd>
    <dt class="property-optional" title="Optional">
        <span>state</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>Any extra arguments used during the lookup.</dd>
    <dt class="property-optional" title="Optional">
        <span>opts</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>A bag of options that control this resource's behavior.</dd>
</dl>

{{% /choosable %}}

{{% choosable language csharp %}}

<dl class="resources-properties">
    <dt class="property-required" title="Required">
        <span>name</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The unique name of the resulting resource.</dd>
    <dt class="property-required" title="Required">
        <span>id</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>The <em>unique</em> provider ID of the resource to lookup.</dd>
    <dt class="property-optional" title="Optional">
        <span>state</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>Any extra arguments used during the lookup.</dd>
    <dt class="property-optional" title="Optional">
        <span>opts</span>
        <span class="property-indicator"></span>
    </dt>
    <dd>A bag of options that control this resource's behavior.</dd>
</dl>

{{% /choosable %}}

The following state arguments are supported:



{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The Amazon Resource Name (ARN) associated of the target.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Batch<wbr>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetbatchtarget">Event<wbr>Target<wbr>Batch<wbr>Target<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke an Amazon Batch Job. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ecs<wbr>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetecstarget">Event<wbr>Target<wbr>Ecs<wbr>Target<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke Amazon ECS Task. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Input</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}Valid JSON text passed to the target.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Input<wbr>Path</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The value of the [JSONPath](http://goessner.net/articles/JsonPath/)
that is used for extracting part of the matched event when passing it to the target.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Input<wbr>Transformer</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetinputtransformer">Event<wbr>Target<wbr>Input<wbr>Transformer<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are providing a custom input to a target based on certain event data.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Kinesis<wbr>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetkinesistarget">Event<wbr>Target<wbr>Kinesis<wbr>Target<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke an Amazon Kinesis Stream. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The Amazon Resource Name (ARN) of the IAM role to be used for this target when the rule is triggered. Required if `ecs_target` is used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Rule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The name of the rule you want to add targets to.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Run<wbr>Command<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetruncommandtarget">List&lt;Event<wbr>Target<wbr>Run<wbr>Command<wbr>Target<wbr>Args&gt;</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke Amazon EC2 Run Command. Documented below. A maximum of 5 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sqs<wbr>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetsqstarget">Event<wbr>Target<wbr>Sqs<wbr>Target<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke an Amazon SQS Queue. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Target<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The unique target assignment ID.  If missing, will generate a random, unique id.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The Amazon Resource Name (ARN) associated of the target.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Batch<wbr>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetbatchtarget">Event<wbr>Target<wbr>Batch<wbr>Target</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke an Amazon Batch Job. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ecs<wbr>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetecstarget">Event<wbr>Target<wbr>Ecs<wbr>Target</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke Amazon ECS Task. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Input</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}Valid JSON text passed to the target.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Input<wbr>Path</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The value of the [JSONPath](http://goessner.net/articles/JsonPath/)
that is used for extracting part of the matched event when passing it to the target.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Input<wbr>Transformer</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetinputtransformer">Event<wbr>Target<wbr>Input<wbr>Transformer</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are providing a custom input to a target based on certain event data.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Kinesis<wbr>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetkinesistarget">Event<wbr>Target<wbr>Kinesis<wbr>Target</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke an Amazon Kinesis Stream. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The Amazon Resource Name (ARN) of the IAM role to be used for this target when the rule is triggered. Required if `ecs_target` is used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Rule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The name of the rule you want to add targets to.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Run<wbr>Command<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetruncommandtarget">[]Event<wbr>Target<wbr>Run<wbr>Command<wbr>Target</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke Amazon EC2 Run Command. Documented below. A maximum of 5 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sqs<wbr>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetsqstarget">Event<wbr>Target<wbr>Sqs<wbr>Target</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke an Amazon SQS Queue. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Target<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The unique target assignment ID.  If missing, will generate a random, unique id.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The Amazon Resource Name (ARN) associated of the target.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>batch<wbr>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetbatchtarget">Event<wbr>Target<wbr>Batch<wbr>Target</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke an Amazon Batch Job. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ecs<wbr>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetecstarget">Event<wbr>Target<wbr>Ecs<wbr>Target</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke Amazon ECS Task. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>input</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}Valid JSON text passed to the target.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>input<wbr>Path</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The value of the [JSONPath](http://goessner.net/articles/JsonPath/)
that is used for extracting part of the matched event when passing it to the target.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>input<wbr>Transformer</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetinputtransformer">Event<wbr>Target<wbr>Input<wbr>Transformer</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are providing a custom input to a target based on certain event data.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>kinesis<wbr>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetkinesistarget">Event<wbr>Target<wbr>Kinesis<wbr>Target</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke an Amazon Kinesis Stream. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>role<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The Amazon Resource Name (ARN) of the IAM role to be used for this target when the rule is triggered. Required if `ecs_target` is used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>rule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The name of the rule you want to add targets to.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>run<wbr>Command<wbr>Targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetruncommandtarget">Event<wbr>Target<wbr>Run<wbr>Command<wbr>Target[]</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke Amazon EC2 Run Command. Documented below. A maximum of 5 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sqs<wbr>Target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetsqstarget">Event<wbr>Target<wbr>Sqs<wbr>Target</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke an Amazon SQS Queue. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>target<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The unique target assignment ID.  If missing, will generate a random, unique id.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The Amazon Resource Name (ARN) associated of the target.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>batch_<wbr>target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetbatchtarget">Dict[Event<wbr>Target<wbr>Batch<wbr>Target]</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke an Amazon Batch Job. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ecs_<wbr>target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetecstarget">Dict[Event<wbr>Target<wbr>Ecs<wbr>Target]</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke Amazon ECS Task. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>input</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}Valid JSON text passed to the target.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>input_<wbr>path</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The value of the [JSONPath](http://goessner.net/articles/JsonPath/)
that is used for extracting part of the matched event when passing it to the target.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>input_<wbr>transformer</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetinputtransformer">Dict[Event<wbr>Target<wbr>Input<wbr>Transformer]</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are providing a custom input to a target based on certain event data.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>kinesis_<wbr>target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetkinesistarget">Dict[Event<wbr>Target<wbr>Kinesis<wbr>Target]</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke an Amazon Kinesis Stream. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>role_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The Amazon Resource Name (ARN) of the IAM role to be used for this target when the rule is triggered. Required if `ecs_target` is used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>rule</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The name of the rule you want to add targets to.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>run_<wbr>command_<wbr>targets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetruncommandtarget">List[Event<wbr>Target<wbr>Run<wbr>Command<wbr>Target]</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke Amazon EC2 Run Command. Documented below. A maximum of 5 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sqs_<wbr>target</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetsqstarget">Dict[Event<wbr>Target<wbr>Sqs<wbr>Target]</a></span>
    </dt>
    <dd>{{% md %}}Parameters used when you are using the rule to invoke an Amazon SQS Queue. Documented below. A maximum of 1 are allowed.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>target_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The unique target assignment ID.  If missing, will generate a random, unique id.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}










## Supporting Types

<h4>Event<wbr>Target<wbr>Batch<wbr>Target</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#EventTargetBatchTarget">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#EventTargetBatchTarget">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/cloudwatch?tab=doc#EventTargetBatchTargetArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/cloudwatch?tab=doc#EventTargetBatchTargetOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Job<wbr>Definition</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The ARN or name of the job definition to use if the event target is an AWS Batch job. This job definition must already exist.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Job<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The name to use for this execution of the job, if the target is an AWS Batch job.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Array<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">int</a></span>
    </dt>
    <dd>{{% md %}}The size of the array, if this is an array batch job. Valid values are integers between 2 and 10,000.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Job<wbr>Attempts</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">int</a></span>
    </dt>
    <dd>{{% md %}}The number of times to attempt to retry, if the job fails. Valid values are 1 to 10.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Job<wbr>Definition</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The ARN or name of the job definition to use if the event target is an AWS Batch job. This job definition must already exist.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Job<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The name to use for this execution of the job, if the target is an AWS Batch job.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Array<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#integer">int</a></span>
    </dt>
    <dd>{{% md %}}The size of the array, if this is an array batch job. Valid values are integers between 2 and 10,000.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Job<wbr>Attempts</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#integer">int</a></span>
    </dt>
    <dd>{{% md %}}The number of times to attempt to retry, if the job fails. Valid values are 1 to 10.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>job<wbr>Definition</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The ARN or name of the job definition to use if the event target is an AWS Batch job. This job definition must already exist.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>job<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The name to use for this execution of the job, if the target is an AWS Batch job.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>array<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/integer">number</a></span>
    </dt>
    <dd>{{% md %}}The size of the array, if this is an array batch job. Valid values are integers between 2 and 10,000.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>job<wbr>Attempts</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/integer">number</a></span>
    </dt>
    <dd>{{% md %}}The number of times to attempt to retry, if the job fails. Valid values are 1 to 10.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>job<wbr>Definition</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The ARN or name of the job definition to use if the event target is an AWS Batch job. This job definition must already exist.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>job<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The name to use for this execution of the job, if the target is an AWS Batch job.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>array<wbr>Size</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">float</a></span>
    </dt>
    <dd>{{% md %}}The size of the array, if this is an array batch job. Valid values are integers between 2 and 10,000.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>job<wbr>Attempts</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">float</a></span>
    </dt>
    <dd>{{% md %}}The number of times to attempt to retry, if the job fails. Valid values are 1 to 10.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Event<wbr>Target<wbr>Ecs<wbr>Target</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#EventTargetEcsTarget">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#EventTargetEcsTarget">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/cloudwatch?tab=doc#EventTargetEcsTargetArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/cloudwatch?tab=doc#EventTargetEcsTargetOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Task<wbr>Definition<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The ARN of the task definition to use if the event target is an Amazon ECS cluster.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Group</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}Specifies an ECS task group for the task. The maximum length is 255 characters.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Launch<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}Specifies the launch type on which your task is running. The launch type that you specify here must match one of the launch type (compatibilities) of the target task. Valid values are EC2 or FARGATE.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Network<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetecstargetnetworkconfiguration">Event<wbr>Target<wbr>Ecs<wbr>Target<wbr>Network<wbr>Configuration<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}Use this if the ECS task uses the awsvpc network mode. This specifies the VPC subnets and security groups associated with the task, and whether a public IP address is to be used. Required if launch_type is FARGATE because the awsvpc mode is required for Fargate tasks.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Platform<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}Specifies the platform version for the task. Specify only the numeric portion of the platform version, such as 1.1.0. This is used only if LaunchType is FARGATE. For more information about valid platform versions, see [AWS Fargate Platform Versions](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/platform_versions.html).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Task<wbr>Count</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">int</a></span>
    </dt>
    <dd>{{% md %}}The number of tasks to create based on the TaskDefinition. The default is 1.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Task<wbr>Definition<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The ARN of the task definition to use if the event target is an Amazon ECS cluster.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Group</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}Specifies an ECS task group for the task. The maximum length is 255 characters.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Launch<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}Specifies the launch type on which your task is running. The launch type that you specify here must match one of the launch type (compatibilities) of the target task. Valid values are EC2 or FARGATE.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Network<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetecstargetnetworkconfiguration">Event<wbr>Target<wbr>Ecs<wbr>Target<wbr>Network<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}Use this if the ECS task uses the awsvpc network mode. This specifies the VPC subnets and security groups associated with the task, and whether a public IP address is to be used. Required if launch_type is FARGATE because the awsvpc mode is required for Fargate tasks.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Platform<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}Specifies the platform version for the task. Specify only the numeric portion of the platform version, such as 1.1.0. This is used only if LaunchType is FARGATE. For more information about valid platform versions, see [AWS Fargate Platform Versions](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/platform_versions.html).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Task<wbr>Count</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#integer">int</a></span>
    </dt>
    <dd>{{% md %}}The number of tasks to create based on the TaskDefinition. The default is 1.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>task<wbr>Definition<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The ARN of the task definition to use if the event target is an Amazon ECS cluster.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>group</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}Specifies an ECS task group for the task. The maximum length is 255 characters.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>launch<wbr>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}Specifies the launch type on which your task is running. The launch type that you specify here must match one of the launch type (compatibilities) of the target task. Valid values are EC2 or FARGATE.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>network<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetecstargetnetworkconfiguration">Event<wbr>Target<wbr>Ecs<wbr>Target<wbr>Network<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}Use this if the ECS task uses the awsvpc network mode. This specifies the VPC subnets and security groups associated with the task, and whether a public IP address is to be used. Required if launch_type is FARGATE because the awsvpc mode is required for Fargate tasks.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>platform<wbr>Version</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}Specifies the platform version for the task. Specify only the numeric portion of the platform version, such as 1.1.0. This is used only if LaunchType is FARGATE. For more information about valid platform versions, see [AWS Fargate Platform Versions](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/platform_versions.html).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>task<wbr>Count</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/integer">number</a></span>
    </dt>
    <dd>{{% md %}}The number of tasks to create based on the TaskDefinition. The default is 1.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>task<wbr>Definition<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The ARN of the task definition to use if the event target is an Amazon ECS cluster.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>group</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}Specifies an ECS task group for the task. The maximum length is 255 characters.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>launch_<wbr>type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}Specifies the launch type on which your task is running. The launch type that you specify here must match one of the launch type (compatibilities) of the target task. Valid values are EC2 or FARGATE.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>network_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#eventtargetecstargetnetworkconfiguration">Dict[Event<wbr>Target<wbr>Ecs<wbr>Target<wbr>Network<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}Use this if the ECS task uses the awsvpc network mode. This specifies the VPC subnets and security groups associated with the task, and whether a public IP address is to be used. Required if launch_type is FARGATE because the awsvpc mode is required for Fargate tasks.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>platform_<wbr>version</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}Specifies the platform version for the task. Specify only the numeric portion of the platform version, such as 1.1.0. This is used only if LaunchType is FARGATE. For more information about valid platform versions, see [AWS Fargate Platform Versions](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/platform_versions.html).
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>task<wbr>Count</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">float</a></span>
    </dt>
    <dd>{{% md %}}The number of tasks to create based on the TaskDefinition. The default is 1.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Event<wbr>Target<wbr>Ecs<wbr>Target<wbr>Network<wbr>Configuration</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#EventTargetEcsTargetNetworkConfiguration">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#EventTargetEcsTargetNetworkConfiguration">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/cloudwatch?tab=doc#EventTargetEcsTargetNetworkConfigurationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/cloudwatch?tab=doc#EventTargetEcsTargetNetworkConfigurationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Subnets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">List&lt;string&gt;</a></span>
    </dt>
    <dd>{{% md %}}The subnets associated with the task or service.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Assign<wbr>Public<wbr>Ip</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">bool</a></span>
    </dt>
    <dd>{{% md %}}Assign a public IP address to the ENI (Fargate launch type only). Valid values are `true` or `false`. Default `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Security<wbr>Groups</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">List&lt;string&gt;</a></span>
    </dt>
    <dd>{{% md %}}The security groups associated with the task or service. If you do not specify a security group, the default security group for the VPC is used.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Subnets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">[]string</a></span>
    </dt>
    <dd>{{% md %}}The subnets associated with the task or service.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Assign<wbr>Public<wbr>Ip</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#boolean">bool</a></span>
    </dt>
    <dd>{{% md %}}Assign a public IP address to the ENI (Fargate launch type only). Valid values are `true` or `false`. Default `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Security<wbr>Groups</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">[]string</a></span>
    </dt>
    <dd>{{% md %}}The security groups associated with the task or service. If you do not specify a security group, the default security group for the VPC is used.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>subnets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string[]</a></span>
    </dt>
    <dd>{{% md %}}The subnets associated with the task or service.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>assign<wbr>Public<wbr>Ip</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/boolean">boolean</a></span>
    </dt>
    <dd>{{% md %}}Assign a public IP address to the ENI (Fargate launch type only). Valid values are `true` or `false`. Default `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>security<wbr>Groups</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string[]</a></span>
    </dt>
    <dd>{{% md %}}The security groups associated with the task or service. If you do not specify a security group, the default security group for the VPC is used.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>subnets</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">List[str]</a></span>
    </dt>
    <dd>{{% md %}}The subnets associated with the task or service.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>assign<wbr>Public<wbr>Ip</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">bool</a></span>
    </dt>
    <dd>{{% md %}}Assign a public IP address to the ENI (Fargate launch type only). Valid values are `true` or `false`. Default `false`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>security_<wbr>groups</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">List[str]</a></span>
    </dt>
    <dd>{{% md %}}The security groups associated with the task or service. If you do not specify a security group, the default security group for the VPC is used.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Event<wbr>Target<wbr>Input<wbr>Transformer</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#EventTargetInputTransformer">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#EventTargetInputTransformer">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/cloudwatch?tab=doc#EventTargetInputTransformerArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/cloudwatch?tab=doc#EventTargetInputTransformerOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Input<wbr>Template</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}Structure containing the template body.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Input<wbr>Paths</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary&lt;string, object&gt;</span>
    </dt>
    <dd>{{% md %}}Key value pairs specified in the form of JSONPath (for example, time = $.time)
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Input<wbr>Template</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}Structure containing the template body.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Input<wbr>Paths</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]interface{}</span>
    </dt>
    <dd>{{% md %}}Key value pairs specified in the form of JSONPath (for example, time = $.time)
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>input<wbr>Template</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}Structure containing the template body.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>input<wbr>Paths</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: any}</span>
    </dt>
    <dd>{{% md %}}Key value pairs specified in the form of JSONPath (for example, time = $.time)
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>input<wbr>Template</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}Structure containing the template body.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>input<wbr>Paths</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}Key value pairs specified in the form of JSONPath (for example, time = $.time)
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Event<wbr>Target<wbr>Kinesis<wbr>Target</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#EventTargetKinesisTarget">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#EventTargetKinesisTarget">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/cloudwatch?tab=doc#EventTargetKinesisTargetArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/cloudwatch?tab=doc#EventTargetKinesisTargetOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Partition<wbr>Key<wbr>Path</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The JSON path to be extracted from the event and used as the partition key.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Partition<wbr>Key<wbr>Path</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The JSON path to be extracted from the event and used as the partition key.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>partition<wbr>Key<wbr>Path</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The JSON path to be extracted from the event and used as the partition key.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>partition<wbr>Key<wbr>Path</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The JSON path to be extracted from the event and used as the partition key.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Event<wbr>Target<wbr>Run<wbr>Command<wbr>Target</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#EventTargetRunCommandTarget">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#EventTargetRunCommandTarget">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/cloudwatch?tab=doc#EventTargetRunCommandTargetArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/cloudwatch?tab=doc#EventTargetRunCommandTargetOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}Can be either `tag:tag-key` or `InstanceIds`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Values</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">List&lt;string&gt;</a></span>
    </dt>
    <dd>{{% md %}}If Key is `tag:tag-key`, Values is a list of tag values. If Key is `InstanceIds`, Values is a list of Amazon EC2 instance IDs.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}Can be either `tag:tag-key` or `InstanceIds`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Values</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">[]string</a></span>
    </dt>
    <dd>{{% md %}}If Key is `tag:tag-key`, Values is a list of tag values. If Key is `InstanceIds`, Values is a list of Amazon EC2 instance IDs.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}Can be either `tag:tag-key` or `InstanceIds`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>values</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string[]</a></span>
    </dt>
    <dd>{{% md %}}If Key is `tag:tag-key`, Values is a list of tag values. If Key is `InstanceIds`, Values is a list of Amazon EC2 instance IDs.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}Can be either `tag:tag-key` or `InstanceIds`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>values</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">List[str]</a></span>
    </dt>
    <dd>{{% md %}}If Key is `tag:tag-key`, Values is a list of tag values. If Key is `InstanceIds`, Values is a list of Amazon EC2 instance IDs.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Event<wbr>Target<wbr>Sqs<wbr>Target</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#EventTargetSqsTarget">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#EventTargetSqsTarget">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/cloudwatch?tab=doc#EventTargetSqsTargetArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/cloudwatch?tab=doc#EventTargetSqsTargetOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Message<wbr>Group<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The FIFO message group ID to use as the target.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Message<wbr>Group<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The FIFO message group ID to use as the target.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>message<wbr>Group<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The FIFO message group ID to use as the target.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>message<wbr>Group<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The FIFO message group ID to use as the target.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}









<h3>Package Details</h3>
<dl class="package-details">
	<dt>Repository</dt>
	<dd><a href="https://github.com/pulumi/pulumi-aws">https://github.com/pulumi/pulumi-aws</a></dd>
	<dt>License</dt>
	<dd>Apache-2.0</dd>
    <dt>Notes</dt>
	<dd>This Pulumi package is based on the [`aws` Terraform Provider](https://github.com/terraform-providers/terraform-provider-aws).</dd>
</dl>

