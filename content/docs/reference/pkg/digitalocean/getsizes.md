
---
title: "GetSizes"
block_external_search_index: true
---



Retrieves information about the Droplet sizes that DigitalOcean supports, with
the ability to filter and sort the results. If no filters are specified, all sizes
will be returned.

{{% examples %}}
{{% /examples %}}





## Using GetSizes

{{< chooser language "javascript,typescript,python,go,csharp" / >}}


{{% choosable language typescript %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">function </span>getSizes<span class="p">(</span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/digitalocean/#GetSizesArgs">GetSizesArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#InvokeOptions">InvokeOptions</a></span><span class="p">): Promise&lt;<span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/digitalocean/#GetSizesResult">GetSizesResult</a></span>></span></code></pre></div>
{{% /choosable %}}


{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">function </span> get_sizes(</span>filters=None<span class="p">, </span>sorts=None<span class="p">, </span>opts=None<span class="p">)</span></code></pre></div>
{{% /choosable %}}


{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>LookupSizes<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v2/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-digitalocean/sdk/v2/go/digitalocean/?tab=doc#GetSizesArgs">GetSizesArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/v2/go/pulumi?tab=doc#InvokeOption">pulumi.InvokeOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-digitalocean/sdk/v2/go/digitalocean/?tab=doc#LookupSizesResult">LookupSizesResult</a></span>, error)</span></code></pre></div>
{{% /choosable %}}


{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static class </span><span class="nx">GetSizes </span><span class="p">{</span><span class="k">
    public static </span>Task&lt;<span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Digitalocean/Pulumi.Digitalocean.GetSizesResult.html">GetSizesResult</a></span>> <span class="p">InvokeAsync(</span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Digitalocean/Pulumi.DigitalOcean.GetSizesArgs.html">GetSizesArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.InvokeOptions.html">InvokeOptions</a></span>? <span class="nx">opts = null<span class="p">)</span><span class="p">
}</span></code></pre></div>
{{% /choosable %}}



The following arguments are supported:



{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Filters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getsizesfilter">List&lt;Pulumi.<wbr>Digital<wbr>Ocean.<wbr>Inputs.<wbr>Get<wbr>Sizes<wbr>Filter<wbr>Args&gt;</a></span>
    </dt>
    <dd>{{% md %}}Filter the results.
The `filter` block is documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sorts</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getsizessort">List&lt;Pulumi.<wbr>Digital<wbr>Ocean.<wbr>Inputs.<wbr>Get<wbr>Sizes<wbr>Sort<wbr>Args&gt;</a></span>
    </dt>
    <dd>{{% md %}}Sort the results.
The `sort` block is documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Filters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getsizesfilter">[]Get<wbr>Sizes<wbr>Filter</a></span>
    </dt>
    <dd>{{% md %}}Filter the results.
The `filter` block is documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Sorts</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getsizessort">[]Get<wbr>Sizes<wbr>Sort</a></span>
    </dt>
    <dd>{{% md %}}Sort the results.
The `sort` block is documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>filters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getsizesfilter">Get<wbr>Sizes<wbr>Filter[]</a></span>
    </dt>
    <dd>{{% md %}}Filter the results.
The `filter` block is documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sorts</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getsizessort">Get<wbr>Sizes<wbr>Sort[]</a></span>
    </dt>
    <dd>{{% md %}}Sort the results.
The `sort` block is documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>filters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getsizesfilter">List[Get<wbr>Sizes<wbr>Filter]</a></span>
    </dt>
    <dd>{{% md %}}Filter the results.
The `filter` block is documented below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>sorts</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getsizessort">List[Get<wbr>Sizes<wbr>Sort]</a></span>
    </dt>
    <dd>{{% md %}}Sort the results.
The `sort` block is documented below.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## GetSizes Result

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}id is the provider-assigned unique ID for this managed resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Sizes</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getsizessize">List&lt;Pulumi.<wbr>Digital<wbr>Ocean.<wbr>Outputs.<wbr>Get<wbr>Sizes<wbr>Size&gt;</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Filters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getsizesfilter">List&lt;Pulumi.<wbr>Digital<wbr>Ocean.<wbr>Outputs.<wbr>Get<wbr>Sizes<wbr>Filter&gt;</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Sorts</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getsizessort">List&lt;Pulumi.<wbr>Digital<wbr>Ocean.<wbr>Outputs.<wbr>Get<wbr>Sizes<wbr>Sort&gt;</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}id is the provider-assigned unique ID for this managed resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Sizes</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getsizessize">[]Get<wbr>Sizes<wbr>Size</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Filters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getsizesfilter">[]Get<wbr>Sizes<wbr>Filter</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Sorts</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getsizessort">[]Get<wbr>Sizes<wbr>Sort</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>id</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}id is the provider-assigned unique ID for this managed resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>sizes</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getsizessize">Get<wbr>Sizes<wbr>Size[]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>filters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getsizesfilter">Get<wbr>Sizes<wbr>Filter[]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>sorts</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getsizessort">Get<wbr>Sizes<wbr>Sort[]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>id</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}id is the provider-assigned unique ID for this managed resource.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>sizes</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getsizessize">List[Get<wbr>Sizes<wbr>Size]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>filters</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getsizesfilter">List[Get<wbr>Sizes<wbr>Filter]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>sorts</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#getsizessort">List[Get<wbr>Sizes<wbr>Sort]</a></span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Supporting Types

<h4>Get<wbr>Sizes<wbr>Filter</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/digitalocean/types/input/#GetSizesFilter">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/digitalocean/types/output/#GetSizesFilter">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-digitalocean/sdk/v2/go/digitalocean/?tab=doc#GetSizesFilterArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-digitalocean/sdk/v2/go/digitalocean/?tab=doc#GetSizesFilter">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}Filter the sizes by this key. This may be one of `slug`,
`regions`, `memory`, `vcpus`, `disk`, `transfer`, `price_monthly`,
`price_hourly`, or `available`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Values</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">List&lt;string&gt;</a></span>
    </dt>
    <dd>{{% md %}}Only retrieves images which keys has value that matches
one of the values provided here.
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
    <dd>{{% md %}}Filter the sizes by this key. This may be one of `slug`,
`regions`, `memory`, `vcpus`, `disk`, `transfer`, `price_monthly`,
`price_hourly`, or `available`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Values</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">[]string</a></span>
    </dt>
    <dd>{{% md %}}Only retrieves images which keys has value that matches
one of the values provided here.
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
    <dd>{{% md %}}Filter the sizes by this key. This may be one of `slug`,
`regions`, `memory`, `vcpus`, `disk`, `transfer`, `price_monthly`,
`price_hourly`, or `available`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>values</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string[]</a></span>
    </dt>
    <dd>{{% md %}}Only retrieves images which keys has value that matches
one of the values provided here.
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
    <dd>{{% md %}}Filter the sizes by this key. This may be one of `slug`,
`regions`, `memory`, `vcpus`, `disk`, `transfer`, `price_monthly`,
`price_hourly`, or `available`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>values</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">List[str]</a></span>
    </dt>
    <dd>{{% md %}}Only retrieves images which keys has value that matches
one of the values provided here.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Get<wbr>Sizes<wbr>Size</h4>
{{% choosable language nodejs %}}
> See the   <a href="/docs/reference/pkg/nodejs/pulumi/digitalocean/types/output/#GetSizesSize">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the   <a href="https://pkg.go.dev/github.com/pulumi/pulumi-digitalocean/sdk/v2/go/digitalocean/?tab=doc#GetSizesSize">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Available</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">bool</a></span>
    </dt>
    <dd>{{% md %}}This represents whether new Droplets can be created with this size.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Disk</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">int</a></span>
    </dt>
    <dd>{{% md %}}The amount of disk space set aside for Droplets of this size. The value is measured in gigabytes.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Memory</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">int</a></span>
    </dt>
    <dd>{{% md %}}The amount of RAM allocated to Droplets created of this size. The value is measured in megabytes.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Price<wbr>Hourly</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">double</a></span>
    </dt>
    <dd>{{% md %}}The hourly cost of Droplets created in this size as measured hourly. The value is measured in US dollars.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Price<wbr>Monthly</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">double</a></span>
    </dt>
    <dd>{{% md %}}The monthly cost of Droplets created in this size if they are kept for an entire month. The value is measured in US dollars.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Regions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">List&lt;string&gt;</a></span>
    </dt>
    <dd>{{% md %}}List of region slugs where Droplets can be created in this size.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Slug</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}A human-readable string that is used to uniquely identify each size.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Transfer</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">double</a></span>
    </dt>
    <dd>{{% md %}}The amount of transfer bandwidth that is available for Droplets created in this size. This only counts traffic on the public interface. The value is given in terabytes.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Vcpus</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">int</a></span>
    </dt>
    <dd>{{% md %}}The number of CPUs allocated to Droplets of this size.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Available</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#boolean">bool</a></span>
    </dt>
    <dd>{{% md %}}This represents whether new Droplets can be created with this size.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Disk</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#integer">int</a></span>
    </dt>
    <dd>{{% md %}}The amount of disk space set aside for Droplets of this size. The value is measured in gigabytes.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Memory</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#integer">int</a></span>
    </dt>
    <dd>{{% md %}}The amount of RAM allocated to Droplets created of this size. The value is measured in megabytes.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Price<wbr>Hourly</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#number">float64</a></span>
    </dt>
    <dd>{{% md %}}The hourly cost of Droplets created in this size as measured hourly. The value is measured in US dollars.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Price<wbr>Monthly</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#number">float64</a></span>
    </dt>
    <dd>{{% md %}}The monthly cost of Droplets created in this size if they are kept for an entire month. The value is measured in US dollars.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Regions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">[]string</a></span>
    </dt>
    <dd>{{% md %}}List of region slugs where Droplets can be created in this size.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Slug</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}A human-readable string that is used to uniquely identify each size.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Transfer</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#number">float64</a></span>
    </dt>
    <dd>{{% md %}}The amount of transfer bandwidth that is available for Droplets created in this size. This only counts traffic on the public interface. The value is given in terabytes.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Vcpus</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#integer">int</a></span>
    </dt>
    <dd>{{% md %}}The number of CPUs allocated to Droplets of this size.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>available</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/boolean">boolean</a></span>
    </dt>
    <dd>{{% md %}}This represents whether new Droplets can be created with this size.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>disk</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/integer">number</a></span>
    </dt>
    <dd>{{% md %}}The amount of disk space set aside for Droplets of this size. The value is measured in gigabytes.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>memory</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/integer">number</a></span>
    </dt>
    <dd>{{% md %}}The amount of RAM allocated to Droplets created of this size. The value is measured in megabytes.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>price<wbr>Hourly</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/number">number</a></span>
    </dt>
    <dd>{{% md %}}The hourly cost of Droplets created in this size as measured hourly. The value is measured in US dollars.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>price<wbr>Monthly</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/number">number</a></span>
    </dt>
    <dd>{{% md %}}The monthly cost of Droplets created in this size if they are kept for an entire month. The value is measured in US dollars.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>regions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string[]</a></span>
    </dt>
    <dd>{{% md %}}List of region slugs where Droplets can be created in this size.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>slug</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}A human-readable string that is used to uniquely identify each size.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>transfer</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/number">number</a></span>
    </dt>
    <dd>{{% md %}}The amount of transfer bandwidth that is available for Droplets created in this size. This only counts traffic on the public interface. The value is given in terabytes.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>vcpus</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/integer">number</a></span>
    </dt>
    <dd>{{% md %}}The number of CPUs allocated to Droplets of this size.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>available</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">bool</a></span>
    </dt>
    <dd>{{% md %}}This represents whether new Droplets can be created with this size.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>disk</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">float</a></span>
    </dt>
    <dd>{{% md %}}The amount of disk space set aside for Droplets of this size. The value is measured in gigabytes.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>memory</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">float</a></span>
    </dt>
    <dd>{{% md %}}The amount of RAM allocated to Droplets created of this size. The value is measured in megabytes.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>price_<wbr>hourly</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">float</a></span>
    </dt>
    <dd>{{% md %}}The hourly cost of Droplets created in this size as measured hourly. The value is measured in US dollars.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>price_<wbr>monthly</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">float</a></span>
    </dt>
    <dd>{{% md %}}The monthly cost of Droplets created in this size if they are kept for an entire month. The value is measured in US dollars.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>regions</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">List[str]</a></span>
    </dt>
    <dd>{{% md %}}List of region slugs where Droplets can be created in this size.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>slug</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}A human-readable string that is used to uniquely identify each size.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>transfer</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">float</a></span>
    </dt>
    <dd>{{% md %}}The amount of transfer bandwidth that is available for Droplets created in this size. This only counts traffic on the public interface. The value is given in terabytes.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>vcpus</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">float</a></span>
    </dt>
    <dd>{{% md %}}The number of CPUs allocated to Droplets of this size.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}





<h4>Get<wbr>Sizes<wbr>Sort</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/digitalocean/types/input/#GetSizesSort">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/digitalocean/types/output/#GetSizesSort">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-digitalocean/sdk/v2/go/digitalocean/?tab=doc#GetSizesSortArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-digitalocean/sdk/v2/go/digitalocean/?tab=doc#GetSizesSort">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Key</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}Sort the sizes by this key. This may be one of `slug`,
`memory`, `vcpus`, `disk`, `transfer`, `price_monthly`, or `price_hourly`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Direction</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span>
    </dt>
    <dd>{{% md %}}The sort direction. This may be either `asc` or `desc`.
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
    <dd>{{% md %}}Sort the sizes by this key. This may be one of `slug`,
`memory`, `vcpus`, `disk`, `transfer`, `price_monthly`, or `price_hourly`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Direction</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://golang.org/pkg/builtin/#string">string</a></span>
    </dt>
    <dd>{{% md %}}The sort direction. This may be either `asc` or `desc`.
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
    <dd>{{% md %}}Sort the sizes by this key. This may be one of `slug`,
`memory`, `vcpus`, `disk`, `transfer`, `price_monthly`, or `price_hourly`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>direction</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span>
    </dt>
    <dd>{{% md %}}The sort direction. This may be either `asc` or `desc`.
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
    <dd>{{% md %}}Sort the sizes by this key. This may be one of `slug`,
`memory`, `vcpus`, `disk`, `transfer`, `price_monthly`, or `price_hourly`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>direction</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="https://docs.python.org/3/library/stdtypes.html">str</a></span>
    </dt>
    <dd>{{% md %}}The sort direction. This may be either `asc` or `desc`.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







