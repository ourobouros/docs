
---
title: "WebAcl"
block_external_search_index: true
---



Provides a WAF Web ACL Resource

{{% examples %}}
## Example Usage
{{% example %}}

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const ipset = new aws.waf.IpSet("ipset", {
    ipSetDescriptors: [{
        type: "IPV4",
        value: "192.0.7.0/24",
    }],
});
const wafrule = new aws.waf.Rule("wafrule", {
    metricName: "tfWAFRule",
    predicates: [{
        dataId: ipset.id,
        negated: false,
        type: "IPMatch",
    }],
}, {dependsOn: [ipset]});
const wafAcl = new aws.waf.WebAcl("waf_acl", {
    defaultAction: {
        type: "ALLOW",
    },
    metricName: "tfWebACL",
    rules: [{
        action: {
            type: "BLOCK",
        },
        priority: 1,
        ruleId: wafrule.id,
        type: "REGULAR",
    }],
}, {dependsOn: [ipset, wafrule]});
```

{{% /example %}}
{{% example %}}
### Logging

> *NOTE:* The Kinesis Firehose Delivery Stream name must begin with `aws-waf-logs-` and be located in `us-east-1` region. See the [AWS WAF Developer Guide](https://docs.aws.amazon.com/waf/latest/developerguide/logging.html) for more information about enabling WAF logging.

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const example = new aws.waf.WebAcl("example", {
    // ... other configuration ...
    loggingConfiguration: {
        logDestination: aws_kinesis_firehose_delivery_stream_example.arn,
        redactedFields: {
            fieldToMatches: [
                {
                    type: "URI",
                },
                {
                    data: "referer",
                    type: "HEADER",
                },
            ],
        },
    },
});
```

{{% /example %}}
{{% /examples %}}



## Create a WebAcl Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/waf/#WebAcl">WebAcl</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/waf/#WebAclArgs">WebAclArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">WebAcl</span><span class="p">(resource_name, opts=None, </span>default_action=None<span class="p">, </span>logging_configuration=None<span class="p">, </span>metric_name=None<span class="p">, </span>name=None<span class="p">, </span>rules=None<span class="p">, </span>tags=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewWebAcl<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v2/go/pulumi?tab=doc#Context">Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/waf?tab=doc#WebAclArgs">WebAclArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v2/go/pulumi?tab=doc#ResourceOption">ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/waf?tab=doc#WebAcl">WebAcl</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Waf.WebAcl.html">WebAcl</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Waf.WebAclArgs.html">WebAclArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Default<wbr>Action</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webacldefaultaction">Web<wbr>Acl<wbr>Default<wbr>Action<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}Configuration block with action that you want AWS WAF to take when a request doesn't match the criteria in any of the rules that are associated with the web ACL. Detailed below.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Metric<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The name or description for the Amazon CloudWatch metric of this web ACL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Logging<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclloggingconfiguration">Web<wbr>Acl<wbr>Logging<wbr>Configuration<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}Configuration block to enable WAF logging. Detailed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The name or description of the web ACL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclrule">List&lt;Web<wbr>Acl<wbr>Rule<wbr>Args&gt;</a></span>
    </dt>
    <dd>{{% md %}}Configuration blocks containing rules to associate with the web ACL and the settings for each rule. Detailed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary&lt;string, object&gt;</span>
    </dt>
    <dd>{{% md %}}Key-value mapping of resource tags
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Default<wbr>Action</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webacldefaultaction">Web<wbr>Acl<wbr>Default<wbr>Action</a></span>
    </dt>
    <dd>{{% md %}}Configuration block with action that you want AWS WAF to take when a request doesn't match the criteria in any of the rules that are associated with the web ACL. Detailed below.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Metric<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The name or description for the Amazon CloudWatch metric of this web ACL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Logging<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclloggingconfiguration">Web<wbr>Acl<wbr>Logging<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}Configuration block to enable WAF logging. Detailed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The name or description of the web ACL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclrule">[]Web<wbr>Acl<wbr>Rule</a></span>
    </dt>
    <dd>{{% md %}}Configuration blocks containing rules to associate with the web ACL and the settings for each rule. Detailed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]interface{}</span>
    </dt>
    <dd>{{% md %}}Key-value mapping of resource tags
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>default<wbr>Action</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webacldefaultaction">Web<wbr>Acl<wbr>Default<wbr>Action</a></span>
    </dt>
    <dd>{{% md %}}Configuration block with action that you want AWS WAF to take when a request doesn't match the criteria in any of the rules that are associated with the web ACL. Detailed below.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>metric<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The name or description for the Amazon CloudWatch metric of this web ACL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>logging<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclloggingconfiguration">Web<wbr>Acl<wbr>Logging<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}Configuration block to enable WAF logging. Detailed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The name or description of the web ACL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclrule">Web<wbr>Acl<wbr>Rule[]</a></span>
    </dt>
    <dd>{{% md %}}Configuration blocks containing rules to associate with the web ACL and the settings for each rule. Detailed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: any}</span>
    </dt>
    <dd>{{% md %}}Key-value mapping of resource tags
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>default_<wbr>action</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webacldefaultaction">Dict[Web<wbr>Acl<wbr>Default<wbr>Action]</a></span>
    </dt>
    <dd>{{% md %}}Configuration block with action that you want AWS WAF to take when a request doesn't match the criteria in any of the rules that are associated with the web ACL. Detailed below.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>metric_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The name or description for the Amazon CloudWatch metric of this web ACL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>logging_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclloggingconfiguration">Dict[Web<wbr>Acl<wbr>Logging<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}Configuration block to enable WAF logging. Detailed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The name or description of the web ACL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclrule">List[Web<wbr>Acl<wbr>Rule]</a></span>
    </dt>
    <dd>{{% md %}}Configuration blocks containing rules to associate with the web ACL and the settings for each rule. Detailed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}Key-value mapping of resource tags
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## WebAcl Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The ARN of the WAF WebACL.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The ARN of the WAF WebACL.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The ARN of the WAF WebACL.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The ARN of the WAF WebACL.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing WebAcl Resource

Get an existing WebAcl resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">Input&lt;ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/waf/#WebAclState">WebAclState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/waf/#WebAcl">WebAcl</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>arn=None<span class="p">, </span>default_action=None<span class="p">, </span>logging_configuration=None<span class="p">, </span>metric_name=None<span class="p">, </span>name=None<span class="p">, </span>rules=None<span class="p">, </span>tags=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetWebAcl<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v2/go/pulumi?tab=doc#Context">Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v2/go/pulumi?tab=doc#IDInput">IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/waf?tab=doc#WebAclState">WebAclState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v2/go/pulumi?tab=doc#ResourceOption">ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/waf?tab=doc#WebAcl">WebAcl</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Waf.WebAcl.html">WebAcl</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Waf.WebAclState.html">WebAclState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
    <dd>{{% md %}}The ARN of the WAF WebACL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Default<wbr>Action</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webacldefaultaction">Web<wbr>Acl<wbr>Default<wbr>Action<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}Configuration block with action that you want AWS WAF to take when a request doesn't match the criteria in any of the rules that are associated with the web ACL. Detailed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Logging<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclloggingconfiguration">Web<wbr>Acl<wbr>Logging<wbr>Configuration<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}Configuration block to enable WAF logging. Detailed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Metric<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The name or description for the Amazon CloudWatch metric of this web ACL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The name or description of the web ACL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclrule">List&lt;Web<wbr>Acl<wbr>Rule<wbr>Args&gt;</a></span>
    </dt>
    <dd>{{% md %}}Configuration blocks containing rules to associate with the web ACL and the settings for each rule. Detailed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dictionary&lt;string, object&gt;</span>
    </dt>
    <dd>{{% md %}}Key-value mapping of resource tags
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
    <dd>{{% md %}}The ARN of the WAF WebACL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Default<wbr>Action</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webacldefaultaction">Web<wbr>Acl<wbr>Default<wbr>Action</a></span>
    </dt>
    <dd>{{% md %}}Configuration block with action that you want AWS WAF to take when a request doesn't match the criteria in any of the rules that are associated with the web ACL. Detailed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Logging<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclloggingconfiguration">Web<wbr>Acl<wbr>Logging<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}Configuration block to enable WAF logging. Detailed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Metric<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The name or description for the Amazon CloudWatch metric of this web ACL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The name or description of the web ACL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclrule">[]Web<wbr>Acl<wbr>Rule</a></span>
    </dt>
    <dd>{{% md %}}Configuration blocks containing rules to associate with the web ACL and the settings for each rule. Detailed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">map[string]interface{}</span>
    </dt>
    <dd>{{% md %}}Key-value mapping of resource tags
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
    <dd>{{% md %}}The ARN of the WAF WebACL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>default<wbr>Action</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webacldefaultaction">Web<wbr>Acl<wbr>Default<wbr>Action</a></span>
    </dt>
    <dd>{{% md %}}Configuration block with action that you want AWS WAF to take when a request doesn't match the criteria in any of the rules that are associated with the web ACL. Detailed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>logging<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclloggingconfiguration">Web<wbr>Acl<wbr>Logging<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}Configuration block to enable WAF logging. Detailed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>metric<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The name or description for the Amazon CloudWatch metric of this web ACL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The name or description of the web ACL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclrule">Web<wbr>Acl<wbr>Rule[]</a></span>
    </dt>
    <dd>{{% md %}}Configuration blocks containing rules to associate with the web ACL and the settings for each rule. Detailed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">{[key: string]: any}</span>
    </dt>
    <dd>{{% md %}}Key-value mapping of resource tags
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
    <dd>{{% md %}}The ARN of the WAF WebACL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>default_<wbr>action</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webacldefaultaction">Dict[Web<wbr>Acl<wbr>Default<wbr>Action]</a></span>
    </dt>
    <dd>{{% md %}}Configuration block with action that you want AWS WAF to take when a request doesn't match the criteria in any of the rules that are associated with the web ACL. Detailed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>logging_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclloggingconfiguration">Dict[Web<wbr>Acl<wbr>Logging<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}Configuration block to enable WAF logging. Detailed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>metric_<wbr>name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The name or description for the Amazon CloudWatch metric of this web ACL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The name or description of the web ACL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>rules</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclrule">List[Web<wbr>Acl<wbr>Rule]</a></span>
    </dt>
    <dd>{{% md %}}Configuration blocks containing rules to associate with the web ACL and the settings for each rule. Detailed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>tags</span>
        <span class="property-indicator"></span>
        <span class="property-type">Dict[str, Any]</span>
    </dt>
    <dd>{{% md %}}Key-value mapping of resource tags
{{% /md %}}</dd>

</dl>
{{% /choosable %}}










## Supporting Types

<h4>Web<wbr>Acl<wbr>Default<wbr>Action</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#WebAclDefaultAction">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#WebAclDefaultAction">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/waf?tab=doc#WebAclDefaultActionArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/waf?tab=doc#WebAclDefaultActionOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The rule type, either `REGULAR`, as defined by [Rule](http://docs.aws.amazon.com/waf/latest/APIReference/API_Rule.html), `RATE_BASED`, as defined by [RateBasedRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_RateBasedRule.html), or `GROUP`, as defined by [RuleGroup](https://docs.aws.amazon.com/waf/latest/APIReference/API_RuleGroup.html). The default is REGULAR. If you add a RATE_BASED rule, you need to set `type` as `RATE_BASED`. If you add a GROUP rule, you need to set `type` as `GROUP`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The rule type, either `REGULAR`, as defined by [Rule](http://docs.aws.amazon.com/waf/latest/APIReference/API_Rule.html), `RATE_BASED`, as defined by [RateBasedRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_RateBasedRule.html), or `GROUP`, as defined by [RuleGroup](https://docs.aws.amazon.com/waf/latest/APIReference/API_RuleGroup.html). The default is REGULAR. If you add a RATE_BASED rule, you need to set `type` as `RATE_BASED`. If you add a GROUP rule, you need to set `type` as `GROUP`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The rule type, either `REGULAR`, as defined by [Rule](http://docs.aws.amazon.com/waf/latest/APIReference/API_Rule.html), `RATE_BASED`, as defined by [RateBasedRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_RateBasedRule.html), or `GROUP`, as defined by [RuleGroup](https://docs.aws.amazon.com/waf/latest/APIReference/API_RuleGroup.html). The default is REGULAR. If you add a RATE_BASED rule, you need to set `type` as `RATE_BASED`. If you add a GROUP rule, you need to set `type` as `GROUP`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The rule type, either `REGULAR`, as defined by [Rule](http://docs.aws.amazon.com/waf/latest/APIReference/API_Rule.html), `RATE_BASED`, as defined by [RateBasedRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_RateBasedRule.html), or `GROUP`, as defined by [RuleGroup](https://docs.aws.amazon.com/waf/latest/APIReference/API_RuleGroup.html). The default is REGULAR. If you add a RATE_BASED rule, you need to set `type` as `RATE_BASED`. If you add a GROUP rule, you need to set `type` as `GROUP`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Web<wbr>Acl<wbr>Logging<wbr>Configuration</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#WebAclLoggingConfiguration">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#WebAclLoggingConfiguration">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/waf?tab=doc#WebAclLoggingConfigurationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/waf?tab=doc#WebAclLoggingConfigurationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Log<wbr>Destination</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of Kinesis Firehose Delivery Stream
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Redacted<wbr>Fields</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclloggingconfigurationredactedfields">Web<wbr>Acl<wbr>Logging<wbr>Configuration<wbr>Redacted<wbr>Fields<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}Configuration block containing parts of the request that you want redacted from the logs. Detailed below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Log<wbr>Destination</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of Kinesis Firehose Delivery Stream
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Redacted<wbr>Fields</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclloggingconfigurationredactedfields">Web<wbr>Acl<wbr>Logging<wbr>Configuration<wbr>Redacted<wbr>Fields</a></span>
    </dt>
    <dd>{{% md %}}Configuration block containing parts of the request that you want redacted from the logs. Detailed below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>log<wbr>Destination</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of Kinesis Firehose Delivery Stream
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>redacted<wbr>Fields</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclloggingconfigurationredactedfields">Web<wbr>Acl<wbr>Logging<wbr>Configuration<wbr>Redacted<wbr>Fields</a></span>
    </dt>
    <dd>{{% md %}}Configuration block containing parts of the request that you want redacted from the logs. Detailed below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>log_<wbr>destination</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of Kinesis Firehose Delivery Stream
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>redacted<wbr>Fields</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclloggingconfigurationredactedfields">Dict[Web<wbr>Acl<wbr>Logging<wbr>Configuration<wbr>Redacted<wbr>Fields]</a></span>
    </dt>
    <dd>{{% md %}}Configuration block containing parts of the request that you want redacted from the logs. Detailed below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Web<wbr>Acl<wbr>Logging<wbr>Configuration<wbr>Redacted<wbr>Fields</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#WebAclLoggingConfigurationRedactedFields">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#WebAclLoggingConfigurationRedactedFields">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/waf?tab=doc#WebAclLoggingConfigurationRedactedFieldsArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/waf?tab=doc#WebAclLoggingConfigurationRedactedFieldsOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Field<wbr>To<wbr>Matches</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclloggingconfigurationredactedfieldsfieldtomatch">List&lt;Web<wbr>Acl<wbr>Logging<wbr>Configuration<wbr>Redacted<wbr>Fields<wbr>Field<wbr>To<wbr>Match<wbr>Args&gt;</a></span>
    </dt>
    <dd>{{% md %}}Set of configuration blocks for fields to redact. Detailed below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Field<wbr>To<wbr>Matches</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclloggingconfigurationredactedfieldsfieldtomatch">[]Web<wbr>Acl<wbr>Logging<wbr>Configuration<wbr>Redacted<wbr>Fields<wbr>Field<wbr>To<wbr>Match</a></span>
    </dt>
    <dd>{{% md %}}Set of configuration blocks for fields to redact. Detailed below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>field<wbr>To<wbr>Matches</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclloggingconfigurationredactedfieldsfieldtomatch">Web<wbr>Acl<wbr>Logging<wbr>Configuration<wbr>Redacted<wbr>Fields<wbr>Field<wbr>To<wbr>Match[]</a></span>
    </dt>
    <dd>{{% md %}}Set of configuration blocks for fields to redact. Detailed below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>field<wbr>To<wbr>Matches</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclloggingconfigurationredactedfieldsfieldtomatch">List[Web<wbr>Acl<wbr>Logging<wbr>Configuration<wbr>Redacted<wbr>Fields<wbr>Field<wbr>To<wbr>Match]</a></span>
    </dt>
    <dd>{{% md %}}Set of configuration blocks for fields to redact. Detailed below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Web<wbr>Acl<wbr>Logging<wbr>Configuration<wbr>Redacted<wbr>Fields<wbr>Field<wbr>To<wbr>Match</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#WebAclLoggingConfigurationRedactedFieldsFieldToMatch">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#WebAclLoggingConfigurationRedactedFieldsFieldToMatch">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/waf?tab=doc#WebAclLoggingConfigurationRedactedFieldsFieldToMatchArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/waf?tab=doc#WebAclLoggingConfigurationRedactedFieldsFieldToMatchOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The rule type, either `REGULAR`, as defined by [Rule](http://docs.aws.amazon.com/waf/latest/APIReference/API_Rule.html), `RATE_BASED`, as defined by [RateBasedRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_RateBasedRule.html), or `GROUP`, as defined by [RuleGroup](https://docs.aws.amazon.com/waf/latest/APIReference/API_RuleGroup.html). The default is REGULAR. If you add a RATE_BASED rule, you need to set `type` as `RATE_BASED`. If you add a GROUP rule, you need to set `type` as `GROUP`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Data</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}When the value of `type` is `HEADER`, enter the name of the header that you want the WAF to search, for example, `User-Agent` or `Referer`. If the value of `type` is any other value, omit `data`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The rule type, either `REGULAR`, as defined by [Rule](http://docs.aws.amazon.com/waf/latest/APIReference/API_Rule.html), `RATE_BASED`, as defined by [RateBasedRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_RateBasedRule.html), or `GROUP`, as defined by [RuleGroup](https://docs.aws.amazon.com/waf/latest/APIReference/API_RuleGroup.html). The default is REGULAR. If you add a RATE_BASED rule, you need to set `type` as `RATE_BASED`. If you add a GROUP rule, you need to set `type` as `GROUP`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Data</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}When the value of `type` is `HEADER`, enter the name of the header that you want the WAF to search, for example, `User-Agent` or `Referer`. If the value of `type` is any other value, omit `data`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The rule type, either `REGULAR`, as defined by [Rule](http://docs.aws.amazon.com/waf/latest/APIReference/API_Rule.html), `RATE_BASED`, as defined by [RateBasedRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_RateBasedRule.html), or `GROUP`, as defined by [RuleGroup](https://docs.aws.amazon.com/waf/latest/APIReference/API_RuleGroup.html). The default is REGULAR. If you add a RATE_BASED rule, you need to set `type` as `RATE_BASED`. If you add a GROUP rule, you need to set `type` as `GROUP`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>data</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}When the value of `type` is `HEADER`, enter the name of the header that you want the WAF to search, for example, `User-Agent` or `Referer`. If the value of `type` is any other value, omit `data`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The rule type, either `REGULAR`, as defined by [Rule](http://docs.aws.amazon.com/waf/latest/APIReference/API_Rule.html), `RATE_BASED`, as defined by [RateBasedRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_RateBasedRule.html), or `GROUP`, as defined by [RuleGroup](https://docs.aws.amazon.com/waf/latest/APIReference/API_RuleGroup.html). The default is REGULAR. If you add a RATE_BASED rule, you need to set `type` as `RATE_BASED`. If you add a GROUP rule, you need to set `type` as `GROUP`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>data</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}When the value of `type` is `HEADER`, enter the name of the header that you want the WAF to search, for example, `User-Agent` or `Referer`. If the value of `type` is any other value, omit `data`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Web<wbr>Acl<wbr>Rule</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#WebAclRule">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#WebAclRule">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/waf?tab=doc#WebAclRuleArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/waf?tab=doc#WebAclRuleOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Priority</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">int</a></span>
    </dt>
    <dd>{{% md %}}Specifies the order in which the rules in a WebACL are evaluated.
Rules with a lower value are evaluated before rules with a higher value.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Rule<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}ID of the associated WAF (Global) rule (e.g. [`aws.waf.Rule`](https://www.terraform.io/docs/providers/aws/r/waf_rule.html)). WAF (Regional) rules cannot be used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Action</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclruleaction">Web<wbr>Acl<wbr>Rule<wbr>Action<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}The action that CloudFront or AWS WAF takes when a web request matches the conditions in the rule. Not used if `type` is `GROUP`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Override<wbr>Action</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclruleoverrideaction">Web<wbr>Acl<wbr>Rule<wbr>Override<wbr>Action<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}Override the action that a group requests CloudFront or AWS WAF takes when a web request matches the conditions in the rule. Only used if `type` is `GROUP`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The rule type, either `REGULAR`, as defined by [Rule](http://docs.aws.amazon.com/waf/latest/APIReference/API_Rule.html), `RATE_BASED`, as defined by [RateBasedRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_RateBasedRule.html), or `GROUP`, as defined by [RuleGroup](https://docs.aws.amazon.com/waf/latest/APIReference/API_RuleGroup.html). The default is REGULAR. If you add a RATE_BASED rule, you need to set `type` as `RATE_BASED`. If you add a GROUP rule, you need to set `type` as `GROUP`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Priority</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#integer">int</a></span>
    </dt>
    <dd>{{% md %}}Specifies the order in which the rules in a WebACL are evaluated.
Rules with a lower value are evaluated before rules with a higher value.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Rule<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}ID of the associated WAF (Global) rule (e.g. [`aws.waf.Rule`](https://www.terraform.io/docs/providers/aws/r/waf_rule.html)). WAF (Regional) rules cannot be used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Action</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclruleaction">Web<wbr>Acl<wbr>Rule<wbr>Action</a></span>
    </dt>
    <dd>{{% md %}}The action that CloudFront or AWS WAF takes when a web request matches the conditions in the rule. Not used if `type` is `GROUP`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Override<wbr>Action</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclruleoverrideaction">Web<wbr>Acl<wbr>Rule<wbr>Override<wbr>Action</a></span>
    </dt>
    <dd>{{% md %}}Override the action that a group requests CloudFront or AWS WAF takes when a web request matches the conditions in the rule. Only used if `type` is `GROUP`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The rule type, either `REGULAR`, as defined by [Rule](http://docs.aws.amazon.com/waf/latest/APIReference/API_Rule.html), `RATE_BASED`, as defined by [RateBasedRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_RateBasedRule.html), or `GROUP`, as defined by [RuleGroup](https://docs.aws.amazon.com/waf/latest/APIReference/API_RuleGroup.html). The default is REGULAR. If you add a RATE_BASED rule, you need to set `type` as `RATE_BASED`. If you add a GROUP rule, you need to set `type` as `GROUP`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>priority</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/integer">number</a></span>
    </dt>
    <dd>{{% md %}}Specifies the order in which the rules in a WebACL are evaluated.
Rules with a lower value are evaluated before rules with a higher value.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>rule<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}ID of the associated WAF (Global) rule (e.g. [`aws.waf.Rule`](https://www.terraform.io/docs/providers/aws/r/waf_rule.html)). WAF (Regional) rules cannot be used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>action</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclruleaction">Web<wbr>Acl<wbr>Rule<wbr>Action</a></span>
    </dt>
    <dd>{{% md %}}The action that CloudFront or AWS WAF takes when a web request matches the conditions in the rule. Not used if `type` is `GROUP`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>override<wbr>Action</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclruleoverrideaction">Web<wbr>Acl<wbr>Rule<wbr>Override<wbr>Action</a></span>
    </dt>
    <dd>{{% md %}}Override the action that a group requests CloudFront or AWS WAF takes when a web request matches the conditions in the rule. Only used if `type` is `GROUP`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The rule type, either `REGULAR`, as defined by [Rule](http://docs.aws.amazon.com/waf/latest/APIReference/API_Rule.html), `RATE_BASED`, as defined by [RateBasedRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_RateBasedRule.html), or `GROUP`, as defined by [RuleGroup](https://docs.aws.amazon.com/waf/latest/APIReference/API_RuleGroup.html). The default is REGULAR. If you add a RATE_BASED rule, you need to set `type` as `RATE_BASED`. If you add a GROUP rule, you need to set `type` as `GROUP`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>priority</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">float</a></span>
    </dt>
    <dd>{{% md %}}Specifies the order in which the rules in a WebACL are evaluated.
Rules with a lower value are evaluated before rules with a higher value.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>rule_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}ID of the associated WAF (Global) rule (e.g. [`aws.waf.Rule`](https://www.terraform.io/docs/providers/aws/r/waf_rule.html)). WAF (Regional) rules cannot be used.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>action</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclruleaction">Dict[Web<wbr>Acl<wbr>Rule<wbr>Action]</a></span>
    </dt>
    <dd>{{% md %}}The action that CloudFront or AWS WAF takes when a web request matches the conditions in the rule. Not used if `type` is `GROUP`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>override<wbr>Action</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#webaclruleoverrideaction">Dict[Web<wbr>Acl<wbr>Rule<wbr>Override<wbr>Action]</a></span>
    </dt>
    <dd>{{% md %}}Override the action that a group requests CloudFront or AWS WAF takes when a web request matches the conditions in the rule. Only used if `type` is `GROUP`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The rule type, either `REGULAR`, as defined by [Rule](http://docs.aws.amazon.com/waf/latest/APIReference/API_Rule.html), `RATE_BASED`, as defined by [RateBasedRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_RateBasedRule.html), or `GROUP`, as defined by [RuleGroup](https://docs.aws.amazon.com/waf/latest/APIReference/API_RuleGroup.html). The default is REGULAR. If you add a RATE_BASED rule, you need to set `type` as `RATE_BASED`. If you add a GROUP rule, you need to set `type` as `GROUP`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Web<wbr>Acl<wbr>Rule<wbr>Action</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#WebAclRuleAction">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#WebAclRuleAction">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/waf?tab=doc#WebAclRuleActionArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/waf?tab=doc#WebAclRuleActionOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The rule type, either `REGULAR`, as defined by [Rule](http://docs.aws.amazon.com/waf/latest/APIReference/API_Rule.html), `RATE_BASED`, as defined by [RateBasedRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_RateBasedRule.html), or `GROUP`, as defined by [RuleGroup](https://docs.aws.amazon.com/waf/latest/APIReference/API_RuleGroup.html). The default is REGULAR. If you add a RATE_BASED rule, you need to set `type` as `RATE_BASED`. If you add a GROUP rule, you need to set `type` as `GROUP`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The rule type, either `REGULAR`, as defined by [Rule](http://docs.aws.amazon.com/waf/latest/APIReference/API_Rule.html), `RATE_BASED`, as defined by [RateBasedRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_RateBasedRule.html), or `GROUP`, as defined by [RuleGroup](https://docs.aws.amazon.com/waf/latest/APIReference/API_RuleGroup.html). The default is REGULAR. If you add a RATE_BASED rule, you need to set `type` as `RATE_BASED`. If you add a GROUP rule, you need to set `type` as `GROUP`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The rule type, either `REGULAR`, as defined by [Rule](http://docs.aws.amazon.com/waf/latest/APIReference/API_Rule.html), `RATE_BASED`, as defined by [RateBasedRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_RateBasedRule.html), or `GROUP`, as defined by [RuleGroup](https://docs.aws.amazon.com/waf/latest/APIReference/API_RuleGroup.html). The default is REGULAR. If you add a RATE_BASED rule, you need to set `type` as `RATE_BASED`. If you add a GROUP rule, you need to set `type` as `GROUP`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The rule type, either `REGULAR`, as defined by [Rule](http://docs.aws.amazon.com/waf/latest/APIReference/API_Rule.html), `RATE_BASED`, as defined by [RateBasedRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_RateBasedRule.html), or `GROUP`, as defined by [RuleGroup](https://docs.aws.amazon.com/waf/latest/APIReference/API_RuleGroup.html). The default is REGULAR. If you add a RATE_BASED rule, you need to set `type` as `RATE_BASED`. If you add a GROUP rule, you need to set `type` as `GROUP`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Web<wbr>Acl<wbr>Rule<wbr>Override<wbr>Action</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#WebAclRuleOverrideAction">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#WebAclRuleOverrideAction">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/waf?tab=doc#WebAclRuleOverrideActionArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/waf?tab=doc#WebAclRuleOverrideActionOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The rule type, either `REGULAR`, as defined by [Rule](http://docs.aws.amazon.com/waf/latest/APIReference/API_Rule.html), `RATE_BASED`, as defined by [RateBasedRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_RateBasedRule.html), or `GROUP`, as defined by [RuleGroup](https://docs.aws.amazon.com/waf/latest/APIReference/API_RuleGroup.html). The default is REGULAR. If you add a RATE_BASED rule, you need to set `type` as `RATE_BASED`. If you add a GROUP rule, you need to set `type` as `GROUP`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The rule type, either `REGULAR`, as defined by [Rule](http://docs.aws.amazon.com/waf/latest/APIReference/API_Rule.html), `RATE_BASED`, as defined by [RateBasedRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_RateBasedRule.html), or `GROUP`, as defined by [RuleGroup](https://docs.aws.amazon.com/waf/latest/APIReference/API_RuleGroup.html). The default is REGULAR. If you add a RATE_BASED rule, you need to set `type` as `RATE_BASED`. If you add a GROUP rule, you need to set `type` as `GROUP`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The rule type, either `REGULAR`, as defined by [Rule](http://docs.aws.amazon.com/waf/latest/APIReference/API_Rule.html), `RATE_BASED`, as defined by [RateBasedRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_RateBasedRule.html), or `GROUP`, as defined by [RuleGroup](https://docs.aws.amazon.com/waf/latest/APIReference/API_RuleGroup.html). The default is REGULAR. If you add a RATE_BASED rule, you need to set `type` as `RATE_BASED`. If you add a GROUP rule, you need to set `type` as `GROUP`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>type</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The rule type, either `REGULAR`, as defined by [Rule](http://docs.aws.amazon.com/waf/latest/APIReference/API_Rule.html), `RATE_BASED`, as defined by [RateBasedRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_RateBasedRule.html), or `GROUP`, as defined by [RuleGroup](https://docs.aws.amazon.com/waf/latest/APIReference/API_RuleGroup.html). The default is REGULAR. If you add a RATE_BASED rule, you need to set `type` as `RATE_BASED`. If you add a GROUP rule, you need to set `type` as `GROUP`.
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

