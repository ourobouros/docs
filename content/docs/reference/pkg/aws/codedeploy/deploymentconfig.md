
---
title: "DeploymentConfig"
block_external_search_index: true
---



Provides a CodeDeploy deployment config for an application

{{% examples %}}
## Example Usage

{{% example %}}
### Server Usage

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const fooDeploymentConfig = new aws.codedeploy.DeploymentConfig("foo", {
    deploymentConfigName: "test-deployment-config",
    minimumHealthyHosts: {
        type: "HOST_COUNT",
        value: 2,
    },
});
const fooDeploymentGroup = new aws.codedeploy.DeploymentGroup("foo", {
    alarmConfiguration: {
        alarms: ["my-alarm-name"],
        enabled: true,
    },
    appName: aws_codedeploy_app_foo_app.name,
    autoRollbackConfiguration: {
        enabled: true,
        events: ["DEPLOYMENT_FAILURE"],
    },
    deploymentConfigName: fooDeploymentConfig.id,
    deploymentGroupName: "bar",
    ec2TagFilters: [{
        key: "filterkey",
        type: "KEY_AND_VALUE",
        value: "filtervalue",
    }],
    serviceRoleArn: aws_iam_role_foo_role.arn,
    triggerConfigurations: [{
        triggerEvents: ["DeploymentFailure"],
        triggerName: "foo-trigger",
        triggerTargetArn: "foo-topic-arn",
    }],
});
```

{{% /example %}}
{{% example %}}
### Lambda Usage

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const fooDeploymentConfig = new aws.codedeploy.DeploymentConfig("foo", {
    computePlatform: "Lambda",
    deploymentConfigName: "test-deployment-config",
    trafficRoutingConfig: {
        timeBasedLinear: {
            interval: 10,
            percentage: 10,
        },
        type: "TimeBasedLinear",
    },
});
const fooDeploymentGroup = new aws.codedeploy.DeploymentGroup("foo", {
    alarmConfiguration: {
        alarms: ["my-alarm-name"],
        enabled: true,
    },
    appName: aws_codedeploy_app_foo_app.name,
    autoRollbackConfiguration: {
        enabled: true,
        events: ["DEPLOYMENT_STOP_ON_ALARM"],
    },
    deploymentConfigName: fooDeploymentConfig.id,
    deploymentGroupName: "bar",
    serviceRoleArn: aws_iam_role_foo_role.arn,
});
```

{{% /example %}}
{{% /examples %}}



## Create a DeploymentConfig Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/codedeploy/#DeploymentConfig">DeploymentConfig</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/codedeploy/#DeploymentConfigArgs">DeploymentConfigArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">DeploymentConfig</span><span class="p">(resource_name, opts=None, </span>compute_platform=None<span class="p">, </span>deployment_config_name=None<span class="p">, </span>minimum_healthy_hosts=None<span class="p">, </span>traffic_routing_config=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewDeploymentConfig<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v2/go/pulumi?tab=doc#Context">Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/codedeploy?tab=doc#DeploymentConfigArgs">DeploymentConfigArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v2/go/pulumi?tab=doc#ResourceOption">ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/codedeploy?tab=doc#DeploymentConfig">DeploymentConfig</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.CodeDeploy.DeploymentConfig.html">DeploymentConfig</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.CodeDeploy.DeploymentConfigArgs.html">DeploymentConfigArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Deployment<wbr>Config<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The name of the deployment config.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Compute<wbr>Platform</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The compute platform can be `Server`, `Lambda`, or `ECS`. Default is `Server`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Minimum<wbr>Healthy<wbr>Hosts</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#deploymentconfigminimumhealthyhosts">Deployment<wbr>Config<wbr>Minimum<wbr>Healthy<wbr>Hosts<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}A minimum_healthy_hosts block. Required for `Server` compute platform. Minimum Healthy Hosts are documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Traffic<wbr>Routing<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#deploymentconfigtrafficroutingconfig">Deployment<wbr>Config<wbr>Traffic<wbr>Routing<wbr>Config<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}A traffic_routing_config block. Traffic Routing Config is documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Deployment<wbr>Config<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The name of the deployment config.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Compute<wbr>Platform</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The compute platform can be `Server`, `Lambda`, or `ECS`. Default is `Server`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Minimum<wbr>Healthy<wbr>Hosts</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#deploymentconfigminimumhealthyhosts">Deployment<wbr>Config<wbr>Minimum<wbr>Healthy<wbr>Hosts</a></span>
    </dt>
    <dd>{{% md %}}A minimum_healthy_hosts block. Required for `Server` compute platform. Minimum Healthy Hosts are documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Traffic<wbr>Routing<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#deploymentconfigtrafficroutingconfig">Deployment<wbr>Config<wbr>Traffic<wbr>Routing<wbr>Config</a></span>
    </dt>
    <dd>{{% md %}}A traffic_routing_config block. Traffic Routing Config is documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>deployment<wbr>Config<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The name of the deployment config.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>compute<wbr>Platform</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The compute platform can be `Server`, `Lambda`, or `ECS`. Default is `Server`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>minimum<wbr>Healthy<wbr>Hosts</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#deploymentconfigminimumhealthyhosts">Deployment<wbr>Config<wbr>Minimum<wbr>Healthy<wbr>Hosts</a></span>
    </dt>
    <dd>{{% md %}}A minimum_healthy_hosts block. Required for `Server` compute platform. Minimum Healthy Hosts are documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>traffic<wbr>Routing<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#deploymentconfigtrafficroutingconfig">Deployment<wbr>Config<wbr>Traffic<wbr>Routing<wbr>Config</a></span>
    </dt>
    <dd>{{% md %}}A traffic_routing_config block. Traffic Routing Config is documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>deployment_<wbr>config_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The name of the deployment config.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>compute_<wbr>platform</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The compute platform can be `Server`, `Lambda`, or `ECS`. Default is `Server`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>minimum_<wbr>healthy_<wbr>hosts</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#deploymentconfigminimumhealthyhosts">Dict[Deployment<wbr>Config<wbr>Minimum<wbr>Healthy<wbr>Hosts]</a></span>
    </dt>
    <dd>{{% md %}}A minimum_healthy_hosts block. Required for `Server` compute platform. Minimum Healthy Hosts are documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>traffic_<wbr>routing_<wbr>config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#deploymentconfigtrafficroutingconfig">Dict[Deployment<wbr>Config<wbr>Traffic<wbr>Routing<wbr>Config]</a></span>
    </dt>
    <dd>{{% md %}}A traffic_routing_config block. Traffic Routing Config is documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## DeploymentConfig Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Deployment<wbr>Config<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The AWS Assigned deployment config id
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Deployment<wbr>Config<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The AWS Assigned deployment config id
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>deployment<wbr>Config<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The AWS Assigned deployment config id
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>deployment_<wbr>config_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The AWS Assigned deployment config id
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing DeploymentConfig Resource

Get an existing DeploymentConfig resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">Input&lt;ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/codedeploy/#DeploymentConfigState">DeploymentConfigState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/codedeploy/#DeploymentConfig">DeploymentConfig</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>compute_platform=None<span class="p">, </span>deployment_config_id=None<span class="p">, </span>deployment_config_name=None<span class="p">, </span>minimum_healthy_hosts=None<span class="p">, </span>traffic_routing_config=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetDeploymentConfig<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v2/go/pulumi?tab=doc#Context">Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v2/go/pulumi?tab=doc#IDInput">IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/codedeploy?tab=doc#DeploymentConfigState">DeploymentConfigState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v2/go/pulumi?tab=doc#ResourceOption">ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/codedeploy?tab=doc#DeploymentConfig">DeploymentConfig</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.CodeDeploy.DeploymentConfig.html">DeploymentConfig</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.CodeDeploy.DeploymentConfigState.html">DeploymentConfigState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Compute<wbr>Platform</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The compute platform can be `Server`, `Lambda`, or `ECS`. Default is `Server`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Deployment<wbr>Config<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The AWS Assigned deployment config id
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Deployment<wbr>Config<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The name of the deployment config.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Minimum<wbr>Healthy<wbr>Hosts</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#deploymentconfigminimumhealthyhosts">Deployment<wbr>Config<wbr>Minimum<wbr>Healthy<wbr>Hosts<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}A minimum_healthy_hosts block. Required for `Server` compute platform. Minimum Healthy Hosts are documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Traffic<wbr>Routing<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#deploymentconfigtrafficroutingconfig">Deployment<wbr>Config<wbr>Traffic<wbr>Routing<wbr>Config<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}A traffic_routing_config block. Traffic Routing Config is documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Compute<wbr>Platform</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The compute platform can be `Server`, `Lambda`, or `ECS`. Default is `Server`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Deployment<wbr>Config<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The AWS Assigned deployment config id
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Deployment<wbr>Config<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The name of the deployment config.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Minimum<wbr>Healthy<wbr>Hosts</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#deploymentconfigminimumhealthyhosts">Deployment<wbr>Config<wbr>Minimum<wbr>Healthy<wbr>Hosts</a></span>
    </dt>
    <dd>{{% md %}}A minimum_healthy_hosts block. Required for `Server` compute platform. Minimum Healthy Hosts are documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Traffic<wbr>Routing<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#deploymentconfigtrafficroutingconfig">Deployment<wbr>Config<wbr>Traffic<wbr>Routing<wbr>Config</a></span>
    </dt>
    <dd>{{% md %}}A traffic_routing_config block. Traffic Routing Config is documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>compute<wbr>Platform</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The compute platform can be `Server`, `Lambda`, or `ECS`. Default is `Server`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>deployment<wbr>Config<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The AWS Assigned deployment config id
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>deployment<wbr>Config<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The name of the deployment config.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>minimum<wbr>Healthy<wbr>Hosts</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#deploymentconfigminimumhealthyhosts">Deployment<wbr>Config<wbr>Minimum<wbr>Healthy<wbr>Hosts</a></span>
    </dt>
    <dd>{{% md %}}A minimum_healthy_hosts block. Required for `Server` compute platform. Minimum Healthy Hosts are documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>traffic<wbr>Routing<wbr>Config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#deploymentconfigtrafficroutingconfig">Deployment<wbr>Config<wbr>Traffic<wbr>Routing<wbr>Config</a></span>
    </dt>
    <dd>{{% md %}}A traffic_routing_config block. Traffic Routing Config is documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>compute_<wbr>platform</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The compute platform can be `Server`, `Lambda`, or `ECS`. Default is `Server`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>deployment_<wbr>config_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The AWS Assigned deployment config id
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>deployment_<wbr>config_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The name of the deployment config.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>minimum_<wbr>healthy_<wbr>hosts</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#deploymentconfigminimumhealthyhosts">Dict[Deployment<wbr>Config<wbr>Minimum<wbr>Healthy<wbr>Hosts]</a></span>
    </dt>
    <dd>{{% md %}}A minimum_healthy_hosts block. Required for `Server` compute platform. Minimum Healthy Hosts are documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>traffic_<wbr>routing_<wbr>config</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#deploymentconfigtrafficroutingconfig">Dict[Deployment<wbr>Config<wbr>Traffic<wbr>Routing<wbr>Config]</a></span>
    </dt>
    <dd>{{% md %}}A traffic_routing_config block. Traffic Routing Config is documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}










## Supporting Types

<h4>Deployment<wbr>Config<wbr>Minimum<wbr>Healthy<wbr>Hosts</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#DeploymentConfigMinimumHealthyHosts">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#DeploymentConfigMinimumHealthyHosts">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/codedeploy?tab=doc#DeploymentConfigMinimumHealthyHostsArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/codedeploy?tab=doc#DeploymentConfigMinimumHealthyHostsOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The type can either be `FLEET_PERCENT` or `HOST_COUNT`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">int</a></span>
    </dt>
    <dd>{{% md %}}The value when the type is `FLEET_PERCENT` represents the minimum number of healthy instances as
a percentage of the total number of instances in the deployment. If you specify FLEET_PERCENT, at the start of the
deployment, AWS CodeDeploy converts the percentage to the equivalent number of instance and rounds up fractional instances.
When the type is `HOST_COUNT`, the value represents the minimum number of healthy instances as an absolute value.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The type can either be `FLEET_PERCENT` or `HOST_COUNT`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#integer">int</a></span>
    </dt>
    <dd>{{% md %}}The value when the type is `FLEET_PERCENT` represents the minimum number of healthy instances as
a percentage of the total number of instances in the deployment. If you specify FLEET_PERCENT, at the start of the
deployment, AWS CodeDeploy converts the percentage to the equivalent number of instance and rounds up fractional instances.
When the type is `HOST_COUNT`, the value represents the minimum number of healthy instances as an absolute value.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The type can either be `FLEET_PERCENT` or `HOST_COUNT`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>value</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/integer">number</a></span>
    </dt>
    <dd>{{% md %}}The value when the type is `FLEET_PERCENT` represents the minimum number of healthy instances as
a percentage of the total number of instances in the deployment. If you specify FLEET_PERCENT, at the start of the
deployment, AWS CodeDeploy converts the percentage to the equivalent number of instance and rounds up fractional instances.
When the type is `HOST_COUNT`, the value represents the minimum number of healthy instances as an absolute value.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The type can either be `FLEET_PERCENT` or `HOST_COUNT`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>value</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">float</a></span>
    </dt>
    <dd>{{% md %}}The value when the type is `FLEET_PERCENT` represents the minimum number of healthy instances as
a percentage of the total number of instances in the deployment. If you specify FLEET_PERCENT, at the start of the
deployment, AWS CodeDeploy converts the percentage to the equivalent number of instance and rounds up fractional instances.
When the type is `HOST_COUNT`, the value represents the minimum number of healthy instances as an absolute value.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Deployment<wbr>Config<wbr>Traffic<wbr>Routing<wbr>Config</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#DeploymentConfigTrafficRoutingConfig">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#DeploymentConfigTrafficRoutingConfig">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/codedeploy?tab=doc#DeploymentConfigTrafficRoutingConfigArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/codedeploy?tab=doc#DeploymentConfigTrafficRoutingConfigOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Time<wbr>Based<wbr>Canary</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#deploymentconfigtrafficroutingconfigtimebasedcanary">Deployment<wbr>Config<wbr>Traffic<wbr>Routing<wbr>Config<wbr>Time<wbr>Based<wbr>Canary<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}The time based canary configuration information. If `type` is `TimeBasedLinear`, use `time_based_linear` instead.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Time<wbr>Based<wbr>Linear</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#deploymentconfigtrafficroutingconfigtimebasedlinear">Deployment<wbr>Config<wbr>Traffic<wbr>Routing<wbr>Config<wbr>Time<wbr>Based<wbr>Linear<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}The time based linear configuration information. If `type` is `TimeBasedCanary`, use `time_based_canary` instead.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}Type of traffic routing config. One of `TimeBasedCanary`, `TimeBasedLinear`, `AllAtOnce`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Time<wbr>Based<wbr>Canary</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#deploymentconfigtrafficroutingconfigtimebasedcanary">Deployment<wbr>Config<wbr>Traffic<wbr>Routing<wbr>Config<wbr>Time<wbr>Based<wbr>Canary</a></span>
    </dt>
    <dd>{{% md %}}The time based canary configuration information. If `type` is `TimeBasedLinear`, use `time_based_linear` instead.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Time<wbr>Based<wbr>Linear</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#deploymentconfigtrafficroutingconfigtimebasedlinear">Deployment<wbr>Config<wbr>Traffic<wbr>Routing<wbr>Config<wbr>Time<wbr>Based<wbr>Linear</a></span>
    </dt>
    <dd>{{% md %}}The time based linear configuration information. If `type` is `TimeBasedCanary`, use `time_based_canary` instead.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}Type of traffic routing config. One of `TimeBasedCanary`, `TimeBasedLinear`, `AllAtOnce`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>time<wbr>Based<wbr>Canary</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#deploymentconfigtrafficroutingconfigtimebasedcanary">Deployment<wbr>Config<wbr>Traffic<wbr>Routing<wbr>Config<wbr>Time<wbr>Based<wbr>Canary</a></span>
    </dt>
    <dd>{{% md %}}The time based canary configuration information. If `type` is `TimeBasedLinear`, use `time_based_linear` instead.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>time<wbr>Based<wbr>Linear</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#deploymentconfigtrafficroutingconfigtimebasedlinear">Deployment<wbr>Config<wbr>Traffic<wbr>Routing<wbr>Config<wbr>Time<wbr>Based<wbr>Linear</a></span>
    </dt>
    <dd>{{% md %}}The time based linear configuration information. If `type` is `TimeBasedCanary`, use `time_based_canary` instead.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}Type of traffic routing config. One of `TimeBasedCanary`, `TimeBasedLinear`, `AllAtOnce`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>time<wbr>Based<wbr>Canary</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#deploymentconfigtrafficroutingconfigtimebasedcanary">Dict[Deployment<wbr>Config<wbr>Traffic<wbr>Routing<wbr>Config<wbr>Time<wbr>Based<wbr>Canary]</a></span>
    </dt>
    <dd>{{% md %}}The time based canary configuration information. If `type` is `TimeBasedLinear`, use `time_based_linear` instead.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>time<wbr>Based<wbr>Linear</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#deploymentconfigtrafficroutingconfigtimebasedlinear">Dict[Deployment<wbr>Config<wbr>Traffic<wbr>Routing<wbr>Config<wbr>Time<wbr>Based<wbr>Linear]</a></span>
    </dt>
    <dd>{{% md %}}The time based linear configuration information. If `type` is `TimeBasedCanary`, use `time_based_canary` instead.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}Type of traffic routing config. One of `TimeBasedCanary`, `TimeBasedLinear`, `AllAtOnce`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Deployment<wbr>Config<wbr>Traffic<wbr>Routing<wbr>Config<wbr>Time<wbr>Based<wbr>Canary</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#DeploymentConfigTrafficRoutingConfigTimeBasedCanary">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#DeploymentConfigTrafficRoutingConfigTimeBasedCanary">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/codedeploy?tab=doc#DeploymentConfigTrafficRoutingConfigTimeBasedCanaryArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/codedeploy?tab=doc#DeploymentConfigTrafficRoutingConfigTimeBasedCanaryOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">int</a></span>
    </dt>
    <dd>{{% md %}}The number of minutes between the first and second traffic shifts of a `TimeBasedCanary` deployment.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Percentage</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">int</a></span>
    </dt>
    <dd>{{% md %}}The percentage of traffic to shift in the first increment of a `TimeBasedCanary` deployment.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#integer">int</a></span>
    </dt>
    <dd>{{% md %}}The number of minutes between the first and second traffic shifts of a `TimeBasedCanary` deployment.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Percentage</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#integer">int</a></span>
    </dt>
    <dd>{{% md %}}The percentage of traffic to shift in the first increment of a `TimeBasedCanary` deployment.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>interval</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/integer">number</a></span>
    </dt>
    <dd>{{% md %}}The number of minutes between the first and second traffic shifts of a `TimeBasedCanary` deployment.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>percentage</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/integer">number</a></span>
    </dt>
    <dd>{{% md %}}The percentage of traffic to shift in the first increment of a `TimeBasedCanary` deployment.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>interval</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">float</a></span>
    </dt>
    <dd>{{% md %}}The number of minutes between the first and second traffic shifts of a `TimeBasedCanary` deployment.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>percentage</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">float</a></span>
    </dt>
    <dd>{{% md %}}The percentage of traffic to shift in the first increment of a `TimeBasedCanary` deployment.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Deployment<wbr>Config<wbr>Traffic<wbr>Routing<wbr>Config<wbr>Time<wbr>Based<wbr>Linear</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#DeploymentConfigTrafficRoutingConfigTimeBasedLinear">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#DeploymentConfigTrafficRoutingConfigTimeBasedLinear">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/codedeploy?tab=doc#DeploymentConfigTrafficRoutingConfigTimeBasedLinearArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/codedeploy?tab=doc#DeploymentConfigTrafficRoutingConfigTimeBasedLinearOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">int</a></span>
    </dt>
    <dd>{{% md %}}The number of minutes between each incremental traffic shift of a `TimeBasedLinear` deployment.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Percentage</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">int</a></span>
    </dt>
    <dd>{{% md %}}The percentage of traffic that is shifted at the start of each increment of a `TimeBasedLinear` deployment.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Interval</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#integer">int</a></span>
    </dt>
    <dd>{{% md %}}The number of minutes between each incremental traffic shift of a `TimeBasedLinear` deployment.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Percentage</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#integer">int</a></span>
    </dt>
    <dd>{{% md %}}The percentage of traffic that is shifted at the start of each increment of a `TimeBasedLinear` deployment.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>interval</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/integer">number</a></span>
    </dt>
    <dd>{{% md %}}The number of minutes between each incremental traffic shift of a `TimeBasedLinear` deployment.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>percentage</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/integer">number</a></span>
    </dt>
    <dd>{{% md %}}The percentage of traffic that is shifted at the start of each increment of a `TimeBasedLinear` deployment.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>interval</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">float</a></span>
    </dt>
    <dd>{{% md %}}The number of minutes between each incremental traffic shift of a `TimeBasedLinear` deployment.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>percentage</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">float</a></span>
    </dt>
    <dd>{{% md %}}The percentage of traffic that is shifted at the start of each increment of a `TimeBasedLinear` deployment.
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

