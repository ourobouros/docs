
---
title: "SecurityConfiguration"
block_external_search_index: true
---



Manages a Glue Security Configuration.

{{% examples %}}
## Example Usage
{{% example %}}

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const example = new aws.glue.SecurityConfiguration("example", {
    encryptionConfiguration: {
        cloudwatchEncryption: {
            cloudwatchEncryptionMode: "DISABLED",
        },
        jobBookmarksEncryption: {
            jobBookmarksEncryptionMode: "DISABLED",
        },
        s3Encryption: {
            kmsKeyArn: aws_kms_key_example.arn,
            s3EncryptionMode: "SSE-KMS",
        },
    },
});
```

{{% /example %}}
{{% /examples %}}



## Create a SecurityConfiguration Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/glue/#SecurityConfiguration">SecurityConfiguration</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/glue/#SecurityConfigurationArgs">SecurityConfigurationArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">SecurityConfiguration</span><span class="p">(resource_name, opts=None, </span>encryption_configuration=None<span class="p">, </span>name=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewSecurityConfiguration<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v2/go/pulumi?tab=doc#Context">Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/glue?tab=doc#SecurityConfigurationArgs">SecurityConfigurationArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v2/go/pulumi?tab=doc#ResourceOption">ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/glue?tab=doc#SecurityConfiguration">SecurityConfiguration</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Glue.SecurityConfiguration.html">SecurityConfiguration</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Glue.SecurityConfigurationArgs.html">SecurityConfigurationArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Encryption<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityconfigurationencryptionconfiguration">Security<wbr>Configuration<wbr>Encryption<wbr>Configuration<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}Configuration block containing encryption configuration. Detailed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}Name of the security configuration.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Encryption<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityconfigurationencryptionconfiguration">Security<wbr>Configuration<wbr>Encryption<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}Configuration block containing encryption configuration. Detailed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}Name of the security configuration.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>encryption<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityconfigurationencryptionconfiguration">Security<wbr>Configuration<wbr>Encryption<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}Configuration block containing encryption configuration. Detailed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}Name of the security configuration.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>encryption_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityconfigurationencryptionconfiguration">Dict[Security<wbr>Configuration<wbr>Encryption<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}Configuration block containing encryption configuration. Detailed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}Name of the security configuration.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}










## Look up an Existing SecurityConfiguration Resource

Get an existing SecurityConfiguration resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">Input&lt;ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/glue/#SecurityConfigurationState">SecurityConfigurationState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/aws/glue/#SecurityConfiguration">SecurityConfiguration</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>encryption_configuration=None<span class="p">, </span>name=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetSecurityConfiguration<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v2/go/pulumi?tab=doc#Context">Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v2/go/pulumi?tab=doc#IDInput">IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/glue?tab=doc#SecurityConfigurationState">SecurityConfigurationState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v2/go/pulumi?tab=doc#ResourceOption">ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/glue?tab=doc#SecurityConfiguration">SecurityConfiguration</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Glue.SecurityConfiguration.html">SecurityConfiguration</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Aws/Pulumi.Aws.Glue.SecurityConfigurationState.html">SecurityConfigurationState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Encryption<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityconfigurationencryptionconfiguration">Security<wbr>Configuration<wbr>Encryption<wbr>Configuration<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}Configuration block containing encryption configuration. Detailed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}Name of the security configuration.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Encryption<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityconfigurationencryptionconfiguration">Security<wbr>Configuration<wbr>Encryption<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}Configuration block containing encryption configuration. Detailed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}Name of the security configuration.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>encryption<wbr>Configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityconfigurationencryptionconfiguration">Security<wbr>Configuration<wbr>Encryption<wbr>Configuration</a></span>
    </dt>
    <dd>{{% md %}}Configuration block containing encryption configuration. Detailed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}Name of the security configuration.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>encryption_<wbr>configuration</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityconfigurationencryptionconfiguration">Dict[Security<wbr>Configuration<wbr>Encryption<wbr>Configuration]</a></span>
    </dt>
    <dd>{{% md %}}Configuration block containing encryption configuration. Detailed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>name</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}Name of the security configuration.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}










## Supporting Types

<h4>Security<wbr>Configuration<wbr>Encryption<wbr>Configuration</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#SecurityConfigurationEncryptionConfiguration">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#SecurityConfigurationEncryptionConfiguration">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/glue?tab=doc#SecurityConfigurationEncryptionConfigurationArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/glue?tab=doc#SecurityConfigurationEncryptionConfigurationOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Cloudwatch<wbr>Encryption</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityconfigurationencryptionconfigurationcloudwatchencryption">Security<wbr>Configuration<wbr>Encryption<wbr>Configuration<wbr>Cloudwatch<wbr>Encryption<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Job<wbr>Bookmarks<wbr>Encryption</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityconfigurationencryptionconfigurationjobbookmarksencryption">Security<wbr>Configuration<wbr>Encryption<wbr>Configuration<wbr>Job<wbr>Bookmarks<wbr>Encryption<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>S3Encryption</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityconfigurationencryptionconfigurations3encryption">Security<wbr>Configuration<wbr>Encryption<wbr>Configuration<wbr>S3Encryption<wbr>Args</a></span>
    </dt>
    <dd>{{% md %}}A `s3_encryption ` block as described below, which contains encryption configuration for S3 data.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Cloudwatch<wbr>Encryption</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityconfigurationencryptionconfigurationcloudwatchencryption">Security<wbr>Configuration<wbr>Encryption<wbr>Configuration<wbr>Cloudwatch<wbr>Encryption</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Job<wbr>Bookmarks<wbr>Encryption</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityconfigurationencryptionconfigurationjobbookmarksencryption">Security<wbr>Configuration<wbr>Encryption<wbr>Configuration<wbr>Job<wbr>Bookmarks<wbr>Encryption</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>S3Encryption</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityconfigurationencryptionconfigurations3encryption">Security<wbr>Configuration<wbr>Encryption<wbr>Configuration<wbr>S3Encryption</a></span>
    </dt>
    <dd>{{% md %}}A `s3_encryption ` block as described below, which contains encryption configuration for S3 data.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>cloudwatch<wbr>Encryption</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityconfigurationencryptionconfigurationcloudwatchencryption">Security<wbr>Configuration<wbr>Encryption<wbr>Configuration<wbr>Cloudwatch<wbr>Encryption</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>job<wbr>Bookmarks<wbr>Encryption</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityconfigurationencryptionconfigurationjobbookmarksencryption">Security<wbr>Configuration<wbr>Encryption<wbr>Configuration<wbr>Job<wbr>Bookmarks<wbr>Encryption</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>s3Encryption</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityconfigurationencryptionconfigurations3encryption">Security<wbr>Configuration<wbr>Encryption<wbr>Configuration<wbr>S3Encryption</a></span>
    </dt>
    <dd>{{% md %}}A `s3_encryption ` block as described below, which contains encryption configuration for S3 data.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>cloudwatch<wbr>Encryption</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityconfigurationencryptionconfigurationcloudwatchencryption">Dict[Security<wbr>Configuration<wbr>Encryption<wbr>Configuration<wbr>Cloudwatch<wbr>Encryption]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>job<wbr>Bookmarks<wbr>Encryption</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityconfigurationencryptionconfigurationjobbookmarksencryption">Dict[Security<wbr>Configuration<wbr>Encryption<wbr>Configuration<wbr>Job<wbr>Bookmarks<wbr>Encryption]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>s3Encryption</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#securityconfigurationencryptionconfigurations3encryption">Dict[Security<wbr>Configuration<wbr>Encryption<wbr>Configuration<wbr>S3Encryption]</a></span>
    </dt>
    <dd>{{% md %}}A `s3_encryption ` block as described below, which contains encryption configuration for S3 data.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Security<wbr>Configuration<wbr>Encryption<wbr>Configuration<wbr>Cloudwatch<wbr>Encryption</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#SecurityConfigurationEncryptionConfigurationCloudwatchEncryption">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#SecurityConfigurationEncryptionConfigurationCloudwatchEncryption">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/glue?tab=doc#SecurityConfigurationEncryptionConfigurationCloudwatchEncryptionArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/glue?tab=doc#SecurityConfigurationEncryptionConfigurationCloudwatchEncryptionOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Cloudwatch<wbr>Encryption<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}Encryption mode to use for CloudWatch data. Valid values: `DISABLED`, `SSE-KMS`. Default value: `DISABLED`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Kms<wbr>Key<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the KMS key to be used to encrypt the data.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Cloudwatch<wbr>Encryption<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}Encryption mode to use for CloudWatch data. Valid values: `DISABLED`, `SSE-KMS`. Default value: `DISABLED`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Kms<wbr>Key<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the KMS key to be used to encrypt the data.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>cloudwatch<wbr>Encryption<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}Encryption mode to use for CloudWatch data. Valid values: `DISABLED`, `SSE-KMS`. Default value: `DISABLED`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>kms<wbr>Key<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the KMS key to be used to encrypt the data.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>cloudwatch<wbr>Encryption<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}Encryption mode to use for CloudWatch data. Valid values: `DISABLED`, `SSE-KMS`. Default value: `DISABLED`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>kms_<wbr>key_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the KMS key to be used to encrypt the data.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Security<wbr>Configuration<wbr>Encryption<wbr>Configuration<wbr>Job<wbr>Bookmarks<wbr>Encryption</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#SecurityConfigurationEncryptionConfigurationJobBookmarksEncryption">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#SecurityConfigurationEncryptionConfigurationJobBookmarksEncryption">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/glue?tab=doc#SecurityConfigurationEncryptionConfigurationJobBookmarksEncryptionArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/glue?tab=doc#SecurityConfigurationEncryptionConfigurationJobBookmarksEncryptionOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Job<wbr>Bookmarks<wbr>Encryption<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}Encryption mode to use for job bookmarks data. Valid values: `CSE-KMS`, `DISABLED`. Default value: `DISABLED`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Kms<wbr>Key<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the KMS key to be used to encrypt the data.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Job<wbr>Bookmarks<wbr>Encryption<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}Encryption mode to use for job bookmarks data. Valid values: `CSE-KMS`, `DISABLED`. Default value: `DISABLED`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Kms<wbr>Key<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the KMS key to be used to encrypt the data.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>job<wbr>Bookmarks<wbr>Encryption<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}Encryption mode to use for job bookmarks data. Valid values: `CSE-KMS`, `DISABLED`. Default value: `DISABLED`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>kms<wbr>Key<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the KMS key to be used to encrypt the data.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>job<wbr>Bookmarks<wbr>Encryption<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}Encryption mode to use for job bookmarks data. Valid values: `CSE-KMS`, `DISABLED`. Default value: `DISABLED`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>kms_<wbr>key_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the KMS key to be used to encrypt the data.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Security<wbr>Configuration<wbr>Encryption<wbr>Configuration<wbr>S3Encryption</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/input/#SecurityConfigurationEncryptionConfigurationS3Encryption">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/aws/types/output/#SecurityConfigurationEncryptionConfigurationS3Encryption">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/glue?tab=doc#SecurityConfigurationEncryptionConfigurationS3EncryptionArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-aws/sdk/v2/go/aws/glue?tab=doc#SecurityConfigurationEncryptionConfigurationS3EncryptionOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Kms<wbr>Key<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the KMS key to be used to encrypt the data.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>S3Encryption<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}Encryption mode to use for S3 data. Valid values: `DISABLED`, `SSE-KMS`, `SSE-S3`. Default value: `DISABLED`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Kms<wbr>Key<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the KMS key to be used to encrypt the data.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>S3Encryption<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}Encryption mode to use for S3 data. Valid values: `DISABLED`, `SSE-KMS`, `SSE-S3`. Default value: `DISABLED`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>kms<wbr>Key<wbr>Arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the KMS key to be used to encrypt the data.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>s3Encryption<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}Encryption mode to use for S3 data. Valid values: `DISABLED`, `SSE-KMS`, `SSE-S3`. Default value: `DISABLED`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>kms_<wbr>key_<wbr>arn</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}Amazon Resource Name (ARN) of the KMS key to be used to encrypt the data.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>s3Encryption<wbr>Mode</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}Encryption mode to use for S3 data. Valid values: `DISABLED`, `SSE-KMS`, `SSE-S3`. Default value: `DISABLED`.
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

