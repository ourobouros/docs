
---
title: "OceanLaunchSpec"
block_external_search_index: true
---



Provides a custom Spotinst Ocean GKE Launch Spec resource.

## Example Usage

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as spotinst from "@pulumi/spotinst";

const example = new spotinst.gke.OceanLaunchSpec("example", {
    autoscaleHeadrooms: [{
        cpuPerUnit: 1000,
        gpuPerUnit: 0,
        memoryPerUnit: 2048,
        numOfUnits: 5,
    }],
    labels: [{
        key: "labelKey",
        value: "labelVal",
    }],
    metadatas: [{
        key: "gci-update-strategy",
        value: "update_disabled",
    }],
    oceanId: "o-123456",
    sourceImage: "image",
    taints: [{
        effect: "taintEffect",
        key: "taintKey",
        value: "taintVal",
    }],
});
```

> This content is derived from https://github.com/terraform-providers/terraform-provider-spotinst/blob/master/website/docs/r/ocean_gke_launch_spec.html.markdown.



## Create a OceanLaunchSpec Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/spotinst/gke/#OceanLaunchSpec">OceanLaunchSpec</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/spotinst/gke/#OceanLaunchSpecArgs">OceanLaunchSpecArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">OceanLaunchSpec</span><span class="p">(resource_name, opts=None, </span>autoscale_headrooms=None<span class="p">, </span>labels=None<span class="p">, </span>metadatas=None<span class="p">, </span>ocean_id=None<span class="p">, </span>source_image=None<span class="p">, </span>taints=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewOceanLaunchSpec<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-spotinst/sdk/go/spotinst/gke?tab=doc#OceanLaunchSpecArgs">OceanLaunchSpecArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-spotinst/sdk/go/spotinst/gke?tab=doc#OceanLaunchSpec">OceanLaunchSpec</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Spotinst/Pulumi.Spotinst.Gke.OceanLaunchSpec.html">OceanLaunchSpec</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Spotinst/Pulumi.Spotinst.Gke.OceanLaunchSpecArgs.html">OceanLaunchSpecArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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

    <dt class="property-optional"
            title="Optional">
        <span>Autoscale<wbr>Headrooms</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspecautoscaleheadroom">List&lt;Ocean<wbr>Launch<wbr>Spec<wbr>Autoscale<wbr>Headroom<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}Set custom headroom per launch spec. provide list of headrooms object.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Labels</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspeclabel">List&lt;Ocean<wbr>Launch<wbr>Spec<wbr>Label<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}Cluster's labels.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Metadatas</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspecmetadata">List&lt;Ocean<wbr>Launch<wbr>Spec<wbr>Metadata<wbr>Args&gt;</a></span>
    </dt>
    <dd>{{% md %}}Cluster's metadata.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Ocean<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Ocean cluster ID required for launchSpec create. 
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Source<wbr>Image</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Image URL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Taints</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspectaint">List&lt;Ocean<wbr>Launch<wbr>Spec<wbr>Taint<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}Cluster's taints.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Autoscale<wbr>Headrooms</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspecautoscaleheadroom">[]Ocean<wbr>Launch<wbr>Spec<wbr>Autoscale<wbr>Headroom</a></span>
    </dt>
    <dd>{{% md %}}Set custom headroom per launch spec. provide list of headrooms object.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Labels</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspeclabel">[]Ocean<wbr>Launch<wbr>Spec<wbr>Label</a></span>
    </dt>
    <dd>{{% md %}}Cluster's labels.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Metadatas</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspecmetadata">[]Ocean<wbr>Launch<wbr>Spec<wbr>Metadata</a></span>
    </dt>
    <dd>{{% md %}}Cluster's metadata.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Ocean<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Ocean cluster ID required for launchSpec create. 
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Source<wbr>Image</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Image URL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Taints</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspectaint">[]Ocean<wbr>Launch<wbr>Spec<wbr>Taint</a></span>
    </dt>
    <dd>{{% md %}}Cluster's taints.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>autoscale<wbr>Headrooms</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspecautoscaleheadroom">Ocean<wbr>Launch<wbr>Spec<wbr>Autoscale<wbr>Headroom[]?</a></span>
    </dt>
    <dd>{{% md %}}Set custom headroom per launch spec. provide list of headrooms object.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>labels</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspeclabel">Ocean<wbr>Launch<wbr>Spec<wbr>Label[]?</a></span>
    </dt>
    <dd>{{% md %}}Cluster's labels.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>metadatas</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspecmetadata">Ocean<wbr>Launch<wbr>Spec<wbr>Metadata[]</a></span>
    </dt>
    <dd>{{% md %}}Cluster's metadata.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>ocean<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Ocean cluster ID required for launchSpec create. 
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>source<wbr>Image</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Image URL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>taints</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspectaint">Ocean<wbr>Launch<wbr>Spec<wbr>Taint[]?</a></span>
    </dt>
    <dd>{{% md %}}Cluster's taints.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>autoscale_<wbr>headrooms</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspecautoscaleheadroom">List[Ocean<wbr>Launch<wbr>Spec<wbr>Autoscale<wbr>Headroom]</a></span>
    </dt>
    <dd>{{% md %}}Set custom headroom per launch spec. provide list of headrooms object.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>labels</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspeclabel">List[Ocean<wbr>Launch<wbr>Spec<wbr>Label]</a></span>
    </dt>
    <dd>{{% md %}}Cluster's labels.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>metadatas</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspecmetadata">List[Ocean<wbr>Launch<wbr>Spec<wbr>Metadata]</a></span>
    </dt>
    <dd>{{% md %}}Cluster's metadata.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>ocean_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The Ocean cluster ID required for launchSpec create. 
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>source_<wbr>image</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Image URL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>taints</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspectaint">List[Ocean<wbr>Launch<wbr>Spec<wbr>Taint]</a></span>
    </dt>
    <dd>{{% md %}}Cluster's taints.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## OceanLaunchSpec Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Autoscale<wbr>Headrooms</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspecautoscaleheadroom">List&lt;Ocean<wbr>Launch<wbr>Spec<wbr>Autoscale<wbr>Headroom&gt;?</a></span>
    </dt>
    <dd>{{% md %}}Set custom headroom per launch spec. provide list of headrooms object.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Labels</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspeclabel">List&lt;Ocean<wbr>Launch<wbr>Spec<wbr>Label&gt;?</a></span>
    </dt>
    <dd>{{% md %}}Cluster's labels.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Metadatas</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspecmetadata">List&lt;Ocean<wbr>Launch<wbr>Spec<wbr>Metadata&gt;</a></span>
    </dt>
    <dd>{{% md %}}Cluster's metadata.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Ocean<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Ocean cluster ID required for launchSpec create. 
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Source<wbr>Image</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Image URL.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Taints</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspectaint">List&lt;Ocean<wbr>Launch<wbr>Spec<wbr>Taint&gt;?</a></span>
    </dt>
    <dd>{{% md %}}Cluster's taints.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Autoscale<wbr>Headrooms</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspecautoscaleheadroom">[]Ocean<wbr>Launch<wbr>Spec<wbr>Autoscale<wbr>Headroom</a></span>
    </dt>
    <dd>{{% md %}}Set custom headroom per launch spec. provide list of headrooms object.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Labels</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspeclabel">[]Ocean<wbr>Launch<wbr>Spec<wbr>Label</a></span>
    </dt>
    <dd>{{% md %}}Cluster's labels.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Metadatas</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspecmetadata">[]Ocean<wbr>Launch<wbr>Spec<wbr>Metadata</a></span>
    </dt>
    <dd>{{% md %}}Cluster's metadata.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Ocean<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Ocean cluster ID required for launchSpec create. 
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Source<wbr>Image</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Image URL.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Taints</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspectaint">[]Ocean<wbr>Launch<wbr>Spec<wbr>Taint</a></span>
    </dt>
    <dd>{{% md %}}Cluster's taints.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>autoscale<wbr>Headrooms</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspecautoscaleheadroom">Ocean<wbr>Launch<wbr>Spec<wbr>Autoscale<wbr>Headroom[]?</a></span>
    </dt>
    <dd>{{% md %}}Set custom headroom per launch spec. provide list of headrooms object.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>labels</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspeclabel">Ocean<wbr>Launch<wbr>Spec<wbr>Label[]?</a></span>
    </dt>
    <dd>{{% md %}}Cluster's labels.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>metadatas</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspecmetadata">Ocean<wbr>Launch<wbr>Spec<wbr>Metadata[]</a></span>
    </dt>
    <dd>{{% md %}}Cluster's metadata.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>ocean<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The Ocean cluster ID required for launchSpec create. 
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>source<wbr>Image</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}Image URL.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>taints</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspectaint">Ocean<wbr>Launch<wbr>Spec<wbr>Taint[]?</a></span>
    </dt>
    <dd>{{% md %}}Cluster's taints.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>autoscale_<wbr>headrooms</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspecautoscaleheadroom">List[Ocean<wbr>Launch<wbr>Spec<wbr>Autoscale<wbr>Headroom]</a></span>
    </dt>
    <dd>{{% md %}}Set custom headroom per launch spec. provide list of headrooms object.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>labels</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspeclabel">List[Ocean<wbr>Launch<wbr>Spec<wbr>Label]</a></span>
    </dt>
    <dd>{{% md %}}Cluster's labels.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>metadatas</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspecmetadata">List[Ocean<wbr>Launch<wbr>Spec<wbr>Metadata]</a></span>
    </dt>
    <dd>{{% md %}}Cluster's metadata.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>ocean_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The Ocean cluster ID required for launchSpec create. 
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>source_<wbr>image</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Image URL.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>taints</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspectaint">List[Ocean<wbr>Launch<wbr>Spec<wbr>Taint]</a></span>
    </dt>
    <dd>{{% md %}}Cluster's taints.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing OceanLaunchSpec Resource

Get an existing OceanLaunchSpec resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">Input&lt;ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/spotinst/gke/#OceanLaunchSpecState">OceanLaunchSpecState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/spotinst/gke/#OceanLaunchSpec">OceanLaunchSpec</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>autoscale_headrooms=None<span class="p">, </span>labels=None<span class="p">, </span>metadatas=None<span class="p">, </span>ocean_id=None<span class="p">, </span>source_image=None<span class="p">, </span>taints=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetOceanLaunchSpec<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-spotinst/sdk/go/spotinst/gke?tab=doc#OceanLaunchSpecState">OceanLaunchSpecState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-spotinst/sdk/go/spotinst/gke?tab=doc#OceanLaunchSpec">OceanLaunchSpec</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Spotinst/Pulumi.Spotinst.Gke.OceanLaunchSpec.html">OceanLaunchSpec</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Spotinst/Pulumi.Spotinst.Gke.OceanLaunchSpecState.html">OceanLaunchSpecState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Autoscale<wbr>Headrooms</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspecautoscaleheadroom">List&lt;Ocean<wbr>Launch<wbr>Spec<wbr>Autoscale<wbr>Headroom<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}Set custom headroom per launch spec. provide list of headrooms object.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Labels</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspeclabel">List&lt;Ocean<wbr>Launch<wbr>Spec<wbr>Label<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}Cluster's labels.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Metadatas</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspecmetadata">List&lt;Ocean<wbr>Launch<wbr>Spec<wbr>Metadata<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}Cluster's metadata.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ocean<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The Ocean cluster ID required for launchSpec create. 
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Source<wbr>Image</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Image URL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Taints</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspectaint">List&lt;Ocean<wbr>Launch<wbr>Spec<wbr>Taint<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}Cluster's taints.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Autoscale<wbr>Headrooms</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspecautoscaleheadroom">[]Ocean<wbr>Launch<wbr>Spec<wbr>Autoscale<wbr>Headroom</a></span>
    </dt>
    <dd>{{% md %}}Set custom headroom per launch spec. provide list of headrooms object.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Labels</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspeclabel">[]Ocean<wbr>Launch<wbr>Spec<wbr>Label</a></span>
    </dt>
    <dd>{{% md %}}Cluster's labels.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Metadatas</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspecmetadata">[]Ocean<wbr>Launch<wbr>Spec<wbr>Metadata</a></span>
    </dt>
    <dd>{{% md %}}Cluster's metadata.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ocean<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The Ocean cluster ID required for launchSpec create. 
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Source<wbr>Image</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}Image URL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Taints</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspectaint">[]Ocean<wbr>Launch<wbr>Spec<wbr>Taint</a></span>
    </dt>
    <dd>{{% md %}}Cluster's taints.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>autoscale<wbr>Headrooms</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspecautoscaleheadroom">Ocean<wbr>Launch<wbr>Spec<wbr>Autoscale<wbr>Headroom[]?</a></span>
    </dt>
    <dd>{{% md %}}Set custom headroom per launch spec. provide list of headrooms object.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>labels</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspeclabel">Ocean<wbr>Launch<wbr>Spec<wbr>Label[]?</a></span>
    </dt>
    <dd>{{% md %}}Cluster's labels.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>metadatas</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspecmetadata">Ocean<wbr>Launch<wbr>Spec<wbr>Metadata[]?</a></span>
    </dt>
    <dd>{{% md %}}Cluster's metadata.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ocean<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The Ocean cluster ID required for launchSpec create. 
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>source<wbr>Image</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}Image URL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>taints</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspectaint">Ocean<wbr>Launch<wbr>Spec<wbr>Taint[]?</a></span>
    </dt>
    <dd>{{% md %}}Cluster's taints.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>autoscale_<wbr>headrooms</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspecautoscaleheadroom">List[Ocean<wbr>Launch<wbr>Spec<wbr>Autoscale<wbr>Headroom]</a></span>
    </dt>
    <dd>{{% md %}}Set custom headroom per launch spec. provide list of headrooms object.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>labels</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspeclabel">List[Ocean<wbr>Launch<wbr>Spec<wbr>Label]</a></span>
    </dt>
    <dd>{{% md %}}Cluster's labels.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>metadatas</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspecmetadata">List[Ocean<wbr>Launch<wbr>Spec<wbr>Metadata]</a></span>
    </dt>
    <dd>{{% md %}}Cluster's metadata.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ocean_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The Ocean cluster ID required for launchSpec create. 
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>source_<wbr>image</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}Image URL.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>taints</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#oceanlaunchspectaint">List[Ocean<wbr>Launch<wbr>Spec<wbr>Taint]</a></span>
    </dt>
    <dd>{{% md %}}Cluster's taints.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}










## Supporting Types

<h4>Ocean<wbr>Launch<wbr>Spec<wbr>Autoscale<wbr>Headroom</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/spotinst/types/input/#OceanLaunchSpecAutoscaleHeadroom">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/spotinst/types/output/#OceanLaunchSpecAutoscaleHeadroom">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-spotinst/sdk/go/spotinst/gke?tab=doc#OceanLaunchSpecAutoscaleHeadroomArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-spotinst/sdk/go/spotinst/gke?tab=doc#OceanLaunchSpecAutoscaleHeadroomOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Cpu<wbr>Per<wbr>Unit</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Optionally configure the number of CPUs to allocate for each headroom unit. CPUs are denoted in millicores, where 1000 millicores = 1 vCPU.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Gpu<wbr>Per<wbr>Unit</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Optionally configure the number of GPUS to allocate for each headroom unit.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Memory<wbr>Per<wbr>Unit</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Optionally configure the amount of memory (MB) to allocate for each headroom unit.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Num<wbr>Of<wbr>Units</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The number of units to retain as headroom, where each unit has the defined headroom CPU, memory and GPU.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Cpu<wbr>Per<wbr>Unit</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Optionally configure the number of CPUs to allocate for each headroom unit. CPUs are denoted in millicores, where 1000 millicores = 1 vCPU.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Gpu<wbr>Per<wbr>Unit</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Optionally configure the number of GPUS to allocate for each headroom unit.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Memory<wbr>Per<wbr>Unit</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Optionally configure the amount of memory (MB) to allocate for each headroom unit.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Num<wbr>Of<wbr>Units</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The number of units to retain as headroom, where each unit has the defined headroom CPU, memory and GPU.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>cpu<wbr>Per<wbr>Unit</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Optionally configure the number of CPUs to allocate for each headroom unit. CPUs are denoted in millicores, where 1000 millicores = 1 vCPU.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>gpu<wbr>Per<wbr>Unit</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Optionally configure the number of GPUS to allocate for each headroom unit.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>memory<wbr>Per<wbr>Unit</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Optionally configure the amount of memory (MB) to allocate for each headroom unit.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>num<wbr>Of<wbr>Units</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}The number of units to retain as headroom, where each unit has the defined headroom CPU, memory and GPU.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>cpu<wbr>Per<wbr>Unit</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Optionally configure the number of CPUs to allocate for each headroom unit. CPUs are denoted in millicores, where 1000 millicores = 1 vCPU.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>gpu<wbr>Per<wbr>Unit</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Optionally configure the number of GPUS to allocate for each headroom unit.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>memory<wbr>Per<wbr>Unit</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Optionally configure the amount of memory (MB) to allocate for each headroom unit.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>num<wbr>Of<wbr>Units</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The number of units to retain as headroom, where each unit has the defined headroom CPU, memory and GPU.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Ocean<wbr>Launch<wbr>Spec<wbr>Label</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/spotinst/types/input/#OceanLaunchSpecLabel">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/spotinst/types/output/#OceanLaunchSpecLabel">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-spotinst/sdk/go/spotinst/gke?tab=doc#OceanLaunchSpecLabelArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-spotinst/sdk/go/spotinst/gke?tab=doc#OceanLaunchSpecLabelOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>value</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>key</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>value</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Ocean<wbr>Launch<wbr>Spec<wbr>Metadata</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/spotinst/types/input/#OceanLaunchSpecMetadata">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/spotinst/types/output/#OceanLaunchSpecMetadata">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-spotinst/sdk/go/spotinst/gke?tab=doc#OceanLaunchSpecMetadataArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-spotinst/sdk/go/spotinst/gke?tab=doc#OceanLaunchSpecMetadataOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>value</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>key</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>value</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Ocean<wbr>Launch<wbr>Spec<wbr>Taint</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/spotinst/types/input/#OceanLaunchSpecTaint">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/spotinst/types/output/#OceanLaunchSpecTaint">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-spotinst/sdk/go/spotinst/gke?tab=doc#OceanLaunchSpecTaintArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-spotinst/sdk/go/spotinst/gke?tab=doc#OceanLaunchSpecTaintOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Effect</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Effect</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Value</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>effect</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>key</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>value</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>effect</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>key</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>value</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}









<h3>Package Details</h3>
<dl class="package-details">
	<dt>Repository</dt>
	<dd><a href="https://github.com/pulumi/pulumi-spotinst">https://github.com/pulumi/pulumi-spotinst</a></dd>
	<dt>License</dt>
	<dd>Apache-2.0</dd>
    
</dl>
