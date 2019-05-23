---
title: Module swf
---

<!-- WARNING: this page was generated by a tool. Do not edit it by hand. -->
<!-- To change it, please see https://github.com/pulumi/docs/tree/master/tools/tscdocgen. -->

<a href="../index.html">@pulumi/aws</a> &gt; swf

<div class="toggleVisible" markdown="1">
<div class="collapsed" markdown="1">
<h2 class="pdoc-module-header toggleButton" title="Click to show Index">Index ▹</h2>
</div>
<div class="expanded" markdown="1">
<h2 class="pdoc-module-header toggleButton" title="Click to hide Index">Index ▾</h2>
<div class="pdoc-module-contents" markdown="1">
* <a href="#Domain">class Domain</a>
* <a href="#DomainArgs">interface DomainArgs</a>
* <a href="#DomainState">interface DomainState</a>

<a href="https://github.com/pulumi/pulumi-aws/blob/a998eb1436459bca87792641e7c9fb49e4a5e61c/sdk/nodejs/swf/domain.ts">swf/domain.ts</a> 
</div>
</div>
</div>


<h2 class="pdoc-module-header" id="Domain">
<a class="pdoc-member-name" href="https://github.com/pulumi/pulumi-aws/blob/a998eb1436459bca87792641e7c9fb49e4a5e61c/sdk/nodejs/swf/domain.ts#L24">class <b>Domain</b></a>
</h2>
<div class="pdoc-module-contents" markdown="1">
<pre class="highlight"><span class='kd'>extends</span> <a href='https://pulumi.io/reference/pkg/nodejs/@pulumi/pulumi/#CustomResource'>CustomResource</a></pre>

Provides an SWF Domain resource.

## Example Usage

To register a basic SWF domain:

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as aws from "@pulumi/aws";

const foo = new aws.swf.Domain("foo", {
    description: "Terraform SWF Domain",
    workflowExecutionRetentionPeriodInDays: "30",
});
```

<h3 class="pdoc-member-header" id="Domain-constructor">
<a class="pdoc-child-name" href="https://github.com/pulumi/pulumi-aws/blob/a998eb1436459bca87792641e7c9fb49e4a5e61c/sdk/nodejs/swf/domain.ts#L52"> <b>constructor</b></a>
</h3>
<div class="pdoc-member-contents" markdown="1">

<pre class="highlight"><span class='kd'></span><span class='kd'>new</span> Domain(name: <span class='kd'><a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String'>string</a></span>, args: <a href='#DomainArgs'>DomainArgs</a>, opts?: <a href='https://pulumi.io/reference/pkg/nodejs/@pulumi/pulumi/#CustomResourceOptions'>pulumi.CustomResourceOptions</a>)</pre>


Create a Domain resource with the given unique name, arguments, and options.

* `name` The _unique_ name of the resource.
* `args` The arguments to use to populate this resource&#39;s properties.
* `opts` A bag of options that control this resource&#39;s behavior.

</div>
<h3 class="pdoc-member-header" id="Domain-get">
<a class="pdoc-child-name" href="https://github.com/pulumi/pulumi-aws/blob/a998eb1436459bca87792641e7c9fb49e4a5e61c/sdk/nodejs/swf/domain.ts#L33">method <b>get</b></a>
</h3>
<div class="pdoc-member-contents" markdown="1">

<pre class="highlight"><span class='kd'>public static </span>get(name: <span class='kd'><a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String'>string</a></span>, id: <a href='https://pulumi.io/reference/pkg/nodejs/@pulumi/pulumi/#Input'>pulumi.Input</a>&lt;<a href='https://pulumi.io/reference/pkg/nodejs/@pulumi/pulumi/#ID'>pulumi.ID</a>&gt;, state?: <a href='#DomainState'>DomainState</a>, opts?: <a href='https://pulumi.io/reference/pkg/nodejs/@pulumi/pulumi/#CustomResourceOptions'>pulumi.CustomResourceOptions</a>): <a href='#Domain'>Domain</a></pre>


Get an existing Domain resource's state with the given name, ID, and optional extra
properties used to qualify the lookup.

</div>
<h3 class="pdoc-member-header" id="Domain-getProvider">
<a class="pdoc-child-name" href="https://github.com/pulumi/pulumi-aws/blob/a998eb1436459bca87792641e7c9fb49e4a5e61c/sdk/nodejs/node_modules/@pulumi/pulumi/resource.d.ts#L14">method <b>getProvider</b></a>
</h3>
<div class="pdoc-member-contents" markdown="1">

<pre class="highlight"><span class='kd'></span>getProvider(moduleMember: <span class='kd'><a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String'>string</a></span>): ProviderResource | <span class='kd'><a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/undefined'>undefined</a></span></pre>

</div>
<h3 class="pdoc-member-header" id="Domain-isInstance">
<a class="pdoc-child-name" href="https://github.com/pulumi/pulumi-aws/blob/a998eb1436459bca87792641e7c9fb49e4a5e61c/sdk/nodejs/node_modules/@pulumi/pulumi/resource.d.ts#L107">method <b>isInstance</b></a>
</h3>
<div class="pdoc-member-contents" markdown="1">

<pre class="highlight"><span class='kd'>static </span>isInstance(obj: <span class='kd'><a href='https://www.typescriptlang.org/docs/handbook/basic-types.html#any'>any</a></span>): <span class='kd'><a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean'>boolean</a></span></pre>


Returns true if the given object is an instance of CustomResource.  This is designed to work even when
multiple copies of the Pulumi SDK have been loaded into the same process.

</div>
<h3 class="pdoc-member-header" id="Domain-description">
<a class="pdoc-child-name" href="https://github.com/pulumi/pulumi-aws/blob/a998eb1436459bca87792641e7c9fb49e4a5e61c/sdk/nodejs/swf/domain.ts#L40">property <b>description</b></a>
</h3>
<div class="pdoc-member-contents" markdown="1">
<pre class="highlight"><span class='kd'>public </span>description: <a href='https://pulumi.io/reference/pkg/nodejs/@pulumi/pulumi/#Output'>pulumi.Output</a>&lt;<span class='kd'><a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String'>string</a></span> | <span class='kd'><a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/undefined'>undefined</a></span>&gt;;</pre>

The domain description.

</div>
<h3 class="pdoc-member-header" id="Domain-id">
<a class="pdoc-child-name" href="https://github.com/pulumi/pulumi-aws/blob/a998eb1436459bca87792641e7c9fb49e4a5e61c/sdk/nodejs/node_modules/@pulumi/pulumi/resource.d.ts#L102">property <b>id</b></a>
</h3>
<div class="pdoc-member-contents" markdown="1">
<pre class="highlight"><span class='kd'></span>id: <a href='https://pulumi.io/reference/pkg/nodejs/@pulumi/pulumi/#Output'>Output</a>&lt;<a href='https://pulumi.io/reference/pkg/nodejs/@pulumi/pulumi/#ID'>ID</a>&gt;;</pre>

id is the provider-assigned unique ID for this managed resource.  It is set during
deployments and may be missing (undefined) during planning phases.

</div>
<h3 class="pdoc-member-header" id="Domain-name">
<a class="pdoc-child-name" href="https://github.com/pulumi/pulumi-aws/blob/a998eb1436459bca87792641e7c9fb49e4a5e61c/sdk/nodejs/swf/domain.ts#L44">property <b>name</b></a>
</h3>
<div class="pdoc-member-contents" markdown="1">
<pre class="highlight"><span class='kd'>public </span>name: <a href='https://pulumi.io/reference/pkg/nodejs/@pulumi/pulumi/#Output'>pulumi.Output</a>&lt;<span class='kd'><a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String'>string</a></span>&gt;;</pre>

The name of the domain. If omitted, Terraform will assign a random, unique name.

</div>
<h3 class="pdoc-member-header" id="Domain-namePrefix">
<a class="pdoc-child-name" href="https://github.com/pulumi/pulumi-aws/blob/a998eb1436459bca87792641e7c9fb49e4a5e61c/sdk/nodejs/swf/domain.ts#L48">property <b>namePrefix</b></a>
</h3>
<div class="pdoc-member-contents" markdown="1">
<pre class="highlight"><span class='kd'>public </span>namePrefix: <a href='https://pulumi.io/reference/pkg/nodejs/@pulumi/pulumi/#Output'>pulumi.Output</a>&lt;<span class='kd'><a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String'>string</a></span> | <span class='kd'><a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/undefined'>undefined</a></span>&gt;;</pre>

Creates a unique name beginning with the specified prefix. Conflicts with `name`.

</div>
<h3 class="pdoc-member-header" id="Domain-urn">
<a class="pdoc-child-name" href="https://github.com/pulumi/pulumi-aws/blob/a998eb1436459bca87792641e7c9fb49e4a5e61c/sdk/nodejs/node_modules/@pulumi/pulumi/resource.d.ts#L12">property <b>urn</b></a>
</h3>
<div class="pdoc-member-contents" markdown="1">
<pre class="highlight"><span class='kd'></span>urn: <a href='https://pulumi.io/reference/pkg/nodejs/@pulumi/pulumi/#Output'>Output</a>&lt;<a href='https://pulumi.io/reference/pkg/nodejs/@pulumi/pulumi/#URN'>URN</a>&gt;;</pre>

urn is the stable logical URN used to distinctly address a resource, both before and after
deployments.

</div>
<h3 class="pdoc-member-header" id="Domain-workflowExecutionRetentionPeriodInDays">
<a class="pdoc-child-name" href="https://github.com/pulumi/pulumi-aws/blob/a998eb1436459bca87792641e7c9fb49e4a5e61c/sdk/nodejs/swf/domain.ts#L52">property <b>workflowExecutionRetentionPeriodInDays</b></a>
</h3>
<div class="pdoc-member-contents" markdown="1">
<pre class="highlight"><span class='kd'>public </span>workflowExecutionRetentionPeriodInDays: <a href='https://pulumi.io/reference/pkg/nodejs/@pulumi/pulumi/#Output'>pulumi.Output</a>&lt;<span class='kd'><a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String'>string</a></span>&gt;;</pre>

Length of time that SWF will continue to retain information about the workflow execution after the workflow execution is complete, must be between 0 and 90 days.

</div>
</div>
<h2 class="pdoc-module-header" id="DomainArgs">
<a class="pdoc-member-name" href="https://github.com/pulumi/pulumi-aws/blob/a998eb1436459bca87792641e7c9fb49e4a5e61c/sdk/nodejs/swf/domain.ts#L109">interface <b>DomainArgs</b></a>
</h2>
<div class="pdoc-module-contents" markdown="1">

The set of arguments for constructing a Domain resource.

<h3 class="pdoc-member-header" id="DomainArgs-description">
<a class="pdoc-child-name" href="https://github.com/pulumi/pulumi-aws/blob/a998eb1436459bca87792641e7c9fb49e4a5e61c/sdk/nodejs/swf/domain.ts#L113">property <b>description</b></a>
</h3>
<div class="pdoc-member-contents" markdown="1">
<pre class="highlight"><span class='kd'></span>description?: <a href='https://pulumi.io/reference/pkg/nodejs/@pulumi/pulumi/#Input'>pulumi.Input</a>&lt;<span class='kd'><a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String'>string</a></span>&gt;;</pre>

The domain description.

</div>
<h3 class="pdoc-member-header" id="DomainArgs-name">
<a class="pdoc-child-name" href="https://github.com/pulumi/pulumi-aws/blob/a998eb1436459bca87792641e7c9fb49e4a5e61c/sdk/nodejs/swf/domain.ts#L117">property <b>name</b></a>
</h3>
<div class="pdoc-member-contents" markdown="1">
<pre class="highlight"><span class='kd'></span>name?: <a href='https://pulumi.io/reference/pkg/nodejs/@pulumi/pulumi/#Input'>pulumi.Input</a>&lt;<span class='kd'><a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String'>string</a></span>&gt;;</pre>

The name of the domain. If omitted, Terraform will assign a random, unique name.

</div>
<h3 class="pdoc-member-header" id="DomainArgs-namePrefix">
<a class="pdoc-child-name" href="https://github.com/pulumi/pulumi-aws/blob/a998eb1436459bca87792641e7c9fb49e4a5e61c/sdk/nodejs/swf/domain.ts#L121">property <b>namePrefix</b></a>
</h3>
<div class="pdoc-member-contents" markdown="1">
<pre class="highlight"><span class='kd'></span>namePrefix?: <a href='https://pulumi.io/reference/pkg/nodejs/@pulumi/pulumi/#Input'>pulumi.Input</a>&lt;<span class='kd'><a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String'>string</a></span>&gt;;</pre>

Creates a unique name beginning with the specified prefix. Conflicts with `name`.

</div>
<h3 class="pdoc-member-header" id="DomainArgs-workflowExecutionRetentionPeriodInDays">
<a class="pdoc-child-name" href="https://github.com/pulumi/pulumi-aws/blob/a998eb1436459bca87792641e7c9fb49e4a5e61c/sdk/nodejs/swf/domain.ts#L125">property <b>workflowExecutionRetentionPeriodInDays</b></a>
</h3>
<div class="pdoc-member-contents" markdown="1">
<pre class="highlight"><span class='kd'></span>workflowExecutionRetentionPeriodInDays: <a href='https://pulumi.io/reference/pkg/nodejs/@pulumi/pulumi/#Input'>pulumi.Input</a>&lt;<span class='kd'><a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String'>string</a></span>&gt;;</pre>

Length of time that SWF will continue to retain information about the workflow execution after the workflow execution is complete, must be between 0 and 90 days.

</div>
</div>
<h2 class="pdoc-module-header" id="DomainState">
<a class="pdoc-member-name" href="https://github.com/pulumi/pulumi-aws/blob/a998eb1436459bca87792641e7c9fb49e4a5e61c/sdk/nodejs/swf/domain.ts#L87">interface <b>DomainState</b></a>
</h2>
<div class="pdoc-module-contents" markdown="1">

Input properties used for looking up and filtering Domain resources.

<h3 class="pdoc-member-header" id="DomainState-description">
<a class="pdoc-child-name" href="https://github.com/pulumi/pulumi-aws/blob/a998eb1436459bca87792641e7c9fb49e4a5e61c/sdk/nodejs/swf/domain.ts#L91">property <b>description</b></a>
</h3>
<div class="pdoc-member-contents" markdown="1">
<pre class="highlight"><span class='kd'></span>description?: <a href='https://pulumi.io/reference/pkg/nodejs/@pulumi/pulumi/#Input'>pulumi.Input</a>&lt;<span class='kd'><a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String'>string</a></span>&gt;;</pre>

The domain description.

</div>
<h3 class="pdoc-member-header" id="DomainState-name">
<a class="pdoc-child-name" href="https://github.com/pulumi/pulumi-aws/blob/a998eb1436459bca87792641e7c9fb49e4a5e61c/sdk/nodejs/swf/domain.ts#L95">property <b>name</b></a>
</h3>
<div class="pdoc-member-contents" markdown="1">
<pre class="highlight"><span class='kd'></span>name?: <a href='https://pulumi.io/reference/pkg/nodejs/@pulumi/pulumi/#Input'>pulumi.Input</a>&lt;<span class='kd'><a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String'>string</a></span>&gt;;</pre>

The name of the domain. If omitted, Terraform will assign a random, unique name.

</div>
<h3 class="pdoc-member-header" id="DomainState-namePrefix">
<a class="pdoc-child-name" href="https://github.com/pulumi/pulumi-aws/blob/a998eb1436459bca87792641e7c9fb49e4a5e61c/sdk/nodejs/swf/domain.ts#L99">property <b>namePrefix</b></a>
</h3>
<div class="pdoc-member-contents" markdown="1">
<pre class="highlight"><span class='kd'></span>namePrefix?: <a href='https://pulumi.io/reference/pkg/nodejs/@pulumi/pulumi/#Input'>pulumi.Input</a>&lt;<span class='kd'><a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String'>string</a></span>&gt;;</pre>

Creates a unique name beginning with the specified prefix. Conflicts with `name`.

</div>
<h3 class="pdoc-member-header" id="DomainState-workflowExecutionRetentionPeriodInDays">
<a class="pdoc-child-name" href="https://github.com/pulumi/pulumi-aws/blob/a998eb1436459bca87792641e7c9fb49e4a5e61c/sdk/nodejs/swf/domain.ts#L103">property <b>workflowExecutionRetentionPeriodInDays</b></a>
</h3>
<div class="pdoc-member-contents" markdown="1">
<pre class="highlight"><span class='kd'></span>workflowExecutionRetentionPeriodInDays?: <a href='https://pulumi.io/reference/pkg/nodejs/@pulumi/pulumi/#Input'>pulumi.Input</a>&lt;<span class='kd'><a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String'>string</a></span>&gt;;</pre>

Length of time that SWF will continue to retain information about the workflow execution after the workflow execution is complete, must be between 0 and 90 days.

</div>
</div>