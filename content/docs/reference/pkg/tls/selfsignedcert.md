
---
title: "SelfSignedCert"
block_external_search_index: true
---






## Create a SelfSignedCert Resource

{{< chooser language "javascript,typescript,python,go,csharp" / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">new </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/tls/#SelfSignedCert">SelfSignedCert</a></span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">args</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/tls/#SelfSignedCertArgs">SelfSignedCertArgs</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">pulumi.CustomResourceOptions</a></span><span class="p">);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">def </span><span class="nf">SelfSignedCert</span><span class="p">(resource_name, opts=None, </span>allowed_uses=None<span class="p">, </span>dns_names=None<span class="p">, </span>early_renewal_hours=None<span class="p">, </span>ip_addresses=None<span class="p">, </span>is_ca_certificate=None<span class="p">, </span>key_algorithm=None<span class="p">, </span>private_key_pem=None<span class="p">, </span>set_subject_key_id=None<span class="p">, </span>subjects=None<span class="p">, </span>uris=None<span class="p">, </span>validity_period_hours=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>NewSelfSignedCert<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">pulumi.Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">args</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-tls/sdk/go/tls/?tab=doc#SelfSignedCertArgs">SelfSignedCertArgs</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">pulumi.ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-tls/sdk/go/tls/?tab=doc#SelfSignedCert">SelfSignedCert</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Tls/Pulumi.Tls..SelfSignedCert.html">SelfSignedCert</a></span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Tls/Pulumi.Tls.SelfSignedCertArgs.html">SelfSignedCertArgs</a></span> <span class="nx">args<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Allowed<wbr>Uses</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string></span>
    </dt>
    <dd>{{% md %}}List of keywords each describing a use that is permitted
for the issued certificate. The valid keywords are listed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Dns<wbr>Names</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of DNS names for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Early<wbr>Renewal<wbr>Hours</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Number of hours before the certificates expiry when a new certificate will be generated
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ip<wbr>Addresses</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of IP addresses for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Is<wbr>Ca<wbr>Certificate</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Boolean controlling whether the CA flag will be set in the
generated certificate. Defaults to `false`, meaning that the certificate does not represent
a certificate authority.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Key<wbr>Algorithm</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the algorithm for the key provided
in `private_key_pem`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Private<wbr>Key<wbr>Pem</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}PEM-encoded private key that the certificate will belong to
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Set<wbr>Subject<wbr>Key<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}If `true`, the certificate will include
the subject key identifier. Defaults to `false`, in which case the subject
key identifier is not set at all.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Subjects</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#selfsignedcertsubject">List&lt;Self<wbr>Signed<wbr>Cert<wbr>Subject<wbr>Args&gt;</a></span>
    </dt>
    <dd>{{% md %}}The subject for which a certificate is being requested.
This is a nested configuration block whose structure matches the
corresponding block for `tls..CertRequest`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Uris</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of URIs for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Validity<wbr>Period<wbr>Hours</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The number of hours after initial issuing that the
certificate will become invalid.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>Allowed<wbr>Uses</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of keywords each describing a use that is permitted
for the issued certificate. The valid keywords are listed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Dns<wbr>Names</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of DNS names for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Early<wbr>Renewal<wbr>Hours</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Number of hours before the certificates expiry when a new certificate will be generated
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ip<wbr>Addresses</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of IP addresses for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Is<wbr>Ca<wbr>Certificate</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Boolean controlling whether the CA flag will be set in the
generated certificate. Defaults to `false`, meaning that the certificate does not represent
a certificate authority.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Key<wbr>Algorithm</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the algorithm for the key provided
in `private_key_pem`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Private<wbr>Key<wbr>Pem</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}PEM-encoded private key that the certificate will belong to
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Set<wbr>Subject<wbr>Key<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}If `true`, the certificate will include
the subject key identifier. Defaults to `false`, in which case the subject
key identifier is not set at all.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Subjects</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#selfsignedcertsubject">[]Self<wbr>Signed<wbr>Cert<wbr>Subject</a></span>
    </dt>
    <dd>{{% md %}}The subject for which a certificate is being requested.
This is a nested configuration block whose structure matches the
corresponding block for `tls..CertRequest`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Uris</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of URIs for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>Validity<wbr>Period<wbr>Hours</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The number of hours after initial issuing that the
certificate will become invalid.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>allowed<wbr>Uses</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]</span>
    </dt>
    <dd>{{% md %}}List of keywords each describing a use that is permitted
for the issued certificate. The valid keywords are listed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>dns<wbr>Names</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of DNS names for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>early<wbr>Renewal<wbr>Hours</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Number of hours before the certificates expiry when a new certificate will be generated
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ip<wbr>Addresses</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of IP addresses for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>is<wbr>Ca<wbr>Certificate</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Boolean controlling whether the CA flag will be set in the
generated certificate. Defaults to `false`, meaning that the certificate does not represent
a certificate authority.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>key<wbr>Algorithm</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the algorithm for the key provided
in `private_key_pem`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>private<wbr>Key<wbr>Pem</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}PEM-encoded private key that the certificate will belong to
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>set<wbr>Subject<wbr>Key<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}If `true`, the certificate will include
the subject key identifier. Defaults to `false`, in which case the subject
key identifier is not set at all.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>subjects</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#selfsignedcertsubject">Self<wbr>Signed<wbr>Cert<wbr>Subject[]</a></span>
    </dt>
    <dd>{{% md %}}The subject for which a certificate is being requested.
This is a nested configuration block whose structure matches the
corresponding block for `tls..CertRequest`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>uris</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of URIs for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>validity<wbr>Period<wbr>Hours</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}The number of hours after initial issuing that the
certificate will become invalid.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-required"
            title="Required">
        <span>allowed_<wbr>uses</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of keywords each describing a use that is permitted
for the issued certificate. The valid keywords are listed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>dns_<wbr>names</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of DNS names for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>early_<wbr>renewal_<wbr>hours</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Number of hours before the certificates expiry when a new certificate will be generated
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ip_<wbr>addresses</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of IP addresses for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>is_<wbr>ca_<wbr>certificate</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Boolean controlling whether the CA flag will be set in the
generated certificate. Defaults to `false`, meaning that the certificate does not represent
a certificate authority.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>key_<wbr>algorithm</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the algorithm for the key provided
in `private_key_pem`.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>private_<wbr>key_<wbr>pem</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}PEM-encoded private key that the certificate will belong to
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>set_<wbr>subject_<wbr>key_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}If `true`, the certificate will include
the subject key identifier. Defaults to `false`, in which case the subject
key identifier is not set at all.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>subjects</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#selfsignedcertsubject">List[Self<wbr>Signed<wbr>Cert<wbr>Subject]</a></span>
    </dt>
    <dd>{{% md %}}The subject for which a certificate is being requested.
This is a nested configuration block whose structure matches the
corresponding block for `tls..CertRequest`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>uris</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of URIs for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-required"
            title="Required">
        <span>validity_<wbr>period_<wbr>hours</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The number of hours after initial issuing that the
certificate will become invalid.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}







## SelfSignedCert Output Properties

The following output properties are available:




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Allowed<wbr>Uses</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string></span>
    </dt>
    <dd>{{% md %}}List of keywords each describing a use that is permitted
for the issued certificate. The valid keywords are listed below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Cert<wbr>Pem</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The certificate data in PEM format.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Dns<wbr>Names</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of DNS names for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Early<wbr>Renewal<wbr>Hours</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Number of hours before the certificates expiry when a new certificate will be generated
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Ip<wbr>Addresses</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of IP addresses for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Is<wbr>Ca<wbr>Certificate</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Boolean controlling whether the CA flag will be set in the
generated certificate. Defaults to `false`, meaning that the certificate does not represent
a certificate authority.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Key<wbr>Algorithm</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the algorithm for the key provided
in `private_key_pem`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Private<wbr>Key<wbr>Pem</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}PEM-encoded private key that the certificate will belong to
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Ready<wbr>For<wbr>Renewal</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Set<wbr>Subject<wbr>Key<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}If `true`, the certificate will include
the subject key identifier. Defaults to `false`, in which case the subject
key identifier is not set at all.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Subjects</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#selfsignedcertsubject">List&lt;Self<wbr>Signed<wbr>Cert<wbr>Subject&gt;</a></span>
    </dt>
    <dd>{{% md %}}The subject for which a certificate is being requested.
This is a nested configuration block whose structure matches the
corresponding block for `tls..CertRequest`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Uris</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of URIs for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Validity<wbr>End<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The time until which the certificate is invalid, as an
[RFC3339](https://tools.ietf.org/html/rfc3339) timestamp.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Validity<wbr>Period<wbr>Hours</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The number of hours after initial issuing that the
certificate will become invalid.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Validity<wbr>Start<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The time after which the certificate is valid, as an
[RFC3339](https://tools.ietf.org/html/rfc3339) timestamp.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>Allowed<wbr>Uses</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of keywords each describing a use that is permitted
for the issued certificate. The valid keywords are listed below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Cert<wbr>Pem</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The certificate data in PEM format.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Dns<wbr>Names</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of DNS names for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Early<wbr>Renewal<wbr>Hours</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Number of hours before the certificates expiry when a new certificate will be generated
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Ip<wbr>Addresses</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of IP addresses for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Is<wbr>Ca<wbr>Certificate</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Boolean controlling whether the CA flag will be set in the
generated certificate. Defaults to `false`, meaning that the certificate does not represent
a certificate authority.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Key<wbr>Algorithm</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the algorithm for the key provided
in `private_key_pem`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Private<wbr>Key<wbr>Pem</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}PEM-encoded private key that the certificate will belong to
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Ready<wbr>For<wbr>Renewal</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Set<wbr>Subject<wbr>Key<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}If `true`, the certificate will include
the subject key identifier. Defaults to `false`, in which case the subject
key identifier is not set at all.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Subjects</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#selfsignedcertsubject">[]Self<wbr>Signed<wbr>Cert<wbr>Subject</a></span>
    </dt>
    <dd>{{% md %}}The subject for which a certificate is being requested.
This is a nested configuration block whose structure matches the
corresponding block for `tls..CertRequest`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Uris</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of URIs for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Validity<wbr>End<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The time until which the certificate is invalid, as an
[RFC3339](https://tools.ietf.org/html/rfc3339) timestamp.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Validity<wbr>Period<wbr>Hours</span>
        <span class="property-indicator"></span>
        <span class="property-type">int</span>
    </dt>
    <dd>{{% md %}}The number of hours after initial issuing that the
certificate will become invalid.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>Validity<wbr>Start<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The time after which the certificate is valid, as an
[RFC3339](https://tools.ietf.org/html/rfc3339) timestamp.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>allowed<wbr>Uses</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]</span>
    </dt>
    <dd>{{% md %}}List of keywords each describing a use that is permitted
for the issued certificate. The valid keywords are listed below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>cert<wbr>Pem</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The certificate data in PEM format.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>dns<wbr>Names</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of DNS names for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>early<wbr>Renewal<wbr>Hours</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Number of hours before the certificates expiry when a new certificate will be generated
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>ip<wbr>Addresses</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of IP addresses for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>is<wbr>Ca<wbr>Certificate</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Boolean controlling whether the CA flag will be set in the
generated certificate. Defaults to `false`, meaning that the certificate does not represent
a certificate authority.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>key<wbr>Algorithm</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The name of the algorithm for the key provided
in `private_key_pem`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>private<wbr>Key<wbr>Pem</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}PEM-encoded private key that the certificate will belong to
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>ready<wbr>For<wbr>Renewal</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>set<wbr>Subject<wbr>Key<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}If `true`, the certificate will include
the subject key identifier. Defaults to `false`, in which case the subject
key identifier is not set at all.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>subjects</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#selfsignedcertsubject">Self<wbr>Signed<wbr>Cert<wbr>Subject[]</a></span>
    </dt>
    <dd>{{% md %}}The subject for which a certificate is being requested.
This is a nested configuration block whose structure matches the
corresponding block for `tls..CertRequest`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>uris</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of URIs for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>validity<wbr>End<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The time until which the certificate is invalid, as an
[RFC3339](https://tools.ietf.org/html/rfc3339) timestamp.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>validity<wbr>Period<wbr>Hours</span>
        <span class="property-indicator"></span>
        <span class="property-type">number</span>
    </dt>
    <dd>{{% md %}}The number of hours after initial issuing that the
certificate will become invalid.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>validity<wbr>Start<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string</span>
    </dt>
    <dd>{{% md %}}The time after which the certificate is valid, as an
[RFC3339](https://tools.ietf.org/html/rfc3339) timestamp.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-"
            title="">
        <span>allowed_<wbr>uses</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of keywords each describing a use that is permitted
for the issued certificate. The valid keywords are listed below.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>cert_<wbr>pem</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The certificate data in PEM format.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>dns_<wbr>names</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of DNS names for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>early_<wbr>renewal_<wbr>hours</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Number of hours before the certificates expiry when a new certificate will be generated
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>ip_<wbr>addresses</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of IP addresses for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>is_<wbr>ca_<wbr>certificate</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Boolean controlling whether the CA flag will be set in the
generated certificate. Defaults to `false`, meaning that the certificate does not represent
a certificate authority.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>key_<wbr>algorithm</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the algorithm for the key provided
in `private_key_pem`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>private_<wbr>key_<wbr>pem</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}PEM-encoded private key that the certificate will belong to
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>ready_<wbr>for_<wbr>renewal</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>set_<wbr>subject_<wbr>key_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}If `true`, the certificate will include
the subject key identifier. Defaults to `false`, in which case the subject
key identifier is not set at all.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>subjects</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#selfsignedcertsubject">List[Self<wbr>Signed<wbr>Cert<wbr>Subject]</a></span>
    </dt>
    <dd>{{% md %}}The subject for which a certificate is being requested.
This is a nested configuration block whose structure matches the
corresponding block for `tls..CertRequest`.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>uris</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of URIs for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>validity_<wbr>end_<wbr>time</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The time until which the certificate is invalid, as an
[RFC3339](https://tools.ietf.org/html/rfc3339) timestamp.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>validity_<wbr>period_<wbr>hours</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The number of hours after initial issuing that the
certificate will become invalid.
{{% /md %}}</dd>

    <dt class="property-"
            title="">
        <span>validity_<wbr>start_<wbr>time</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The time after which the certificate is valid, as an
[RFC3339](https://tools.ietf.org/html/rfc3339) timestamp.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}








## Look up an Existing SelfSignedCert Resource

Get an existing SelfSignedCert resource's state with the given name, ID, and optional extra properties used to qualify the lookup.

{{< chooser language "javascript,typescript,python,go,csharp  " / >}}

{{% choosable language nodejs %}}
<div class="highlight"><pre class="chroma"><code class="language-typescript" data-lang="typescript"><span class="k">public static </span><span class="nf">get</span><span class="p">(</span><span class="nx">name</span>: <span class="nx"><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/string">string</a></span><span class="p">, </span><span class="nx">id</span>: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#ID">Input&lt;ID&gt;</a></span><span class="p">, </span><span class="nx">state</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/tls/#SelfSignedCertState">SelfSignedCertState</a></span><span class="p">, </span><span class="nx">opts</span>?: <span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/pulumi/#CustomResourceOptions">CustomResourceOptions</a></span><span class="p">): </span><span class="nx"><a href="/docs/reference/pkg/nodejs/pulumi/tls/#SelfSignedCert">SelfSignedCert</a></span></code></pre></div>
{{% /choosable %}}

{{% choosable language python %}}
<div class="highlight"><pre class="chroma"><code class="language-python" data-lang="python"><span class="k">static </span><span class="nf">get</span><span class="p">(resource_name, id, opts=None, </span>allowed_uses=None<span class="p">, </span>cert_pem=None<span class="p">, </span>dns_names=None<span class="p">, </span>early_renewal_hours=None<span class="p">, </span>ip_addresses=None<span class="p">, </span>is_ca_certificate=None<span class="p">, </span>key_algorithm=None<span class="p">, </span>private_key_pem=None<span class="p">, </span>ready_for_renewal=None<span class="p">, </span>set_subject_key_id=None<span class="p">, </span>subjects=None<span class="p">, </span>uris=None<span class="p">, </span>validity_end_time=None<span class="p">, </span>validity_period_hours=None<span class="p">, </span>validity_start_time=None<span class="p">, __props__=None);</span></code></pre></div>
{{% /choosable %}}

{{% choosable language go %}}
<div class="highlight"><pre class="chroma"><code class="language-go" data-lang="go"><span class="k">func </span>GetSelfSignedCert<span class="p">(</span><span class="nx">ctx</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#Context">Context</a></span><span class="p">, </span><span class="nx">name</span> <span class="nx"><a href="https://golang.org/pkg/builtin/#string">string</a></span><span class="p">, </span><span class="nx">id</span> <span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#IDInput">IDInput</a></span><span class="p">, </span><span class="nx">state</span> *<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-tls/sdk/go/tls/?tab=doc#SelfSignedCertState">SelfSignedCertState</a></span><span class="p">, </span><span class="nx">opts</span> ...<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi/sdk/go/pulumi?tab=doc#ResourceOption">ResourceOption</a></span><span class="p">) (*<span class="nx"><a href="https://pkg.go.dev/github.com/pulumi/pulumi-tls/sdk/go/tls/?tab=doc#SelfSignedCert">SelfSignedCert</a></span>, error)</span></code></pre></div>
{{% /choosable %}}

{{% choosable language csharp %}}
<div class="highlight"><pre class="chroma"><code class="language-csharp" data-lang="csharp"><span class="k">public static </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Tls/Pulumi.Tls..SelfSignedCert.html">SelfSignedCert</a></span><span class="nf"> Get</span><span class="p">(</span><span class="nx"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types">string</a></span> <span class="nx">name<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.Input.html">Input&lt;string&gt;</a></span> <span class="nx">id<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi.Tls/Pulumi.Tls..SelfSignedCertState.html">SelfSignedCertState</a></span>? <span class="nx">state<span class="p">, </span><span class="nx"><a href="/docs/reference/pkg/dotnet/Pulumi/Pulumi.CustomResourceOptions.html">CustomResourceOptions</a></span>? <span class="nx">opts = null<span class="p">)</span></code></pre></div>
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
        <span>Allowed<wbr>Uses</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of keywords each describing a use that is permitted
for the issued certificate. The valid keywords are listed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Cert<wbr>Pem</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The certificate data in PEM format.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Dns<wbr>Names</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of DNS names for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Early<wbr>Renewal<wbr>Hours</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}Number of hours before the certificates expiry when a new certificate will be generated
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ip<wbr>Addresses</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of IP addresses for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Is<wbr>Ca<wbr>Certificate</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}Boolean controlling whether the CA flag will be set in the
generated certificate. Defaults to `false`, meaning that the certificate does not represent
a certificate authority.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Key<wbr>Algorithm</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the algorithm for the key provided
in `private_key_pem`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Private<wbr>Key<wbr>Pem</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}PEM-encoded private key that the certificate will belong to
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ready<wbr>For<wbr>Renewal</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Set<wbr>Subject<wbr>Key<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool?</span>
    </dt>
    <dd>{{% md %}}If `true`, the certificate will include
the subject key identifier. Defaults to `false`, in which case the subject
key identifier is not set at all.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Subjects</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#selfsignedcertsubject">List&lt;Self<wbr>Signed<wbr>Cert<wbr>Subject<wbr>Args&gt;?</a></span>
    </dt>
    <dd>{{% md %}}The subject for which a certificate is being requested.
This is a nested configuration block whose structure matches the
corresponding block for `tls..CertRequest`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Uris</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}List of URIs for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Validity<wbr>End<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The time until which the certificate is invalid, as an
[RFC3339](https://tools.ietf.org/html/rfc3339) timestamp.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Validity<wbr>Period<wbr>Hours</span>
        <span class="property-indicator"></span>
        <span class="property-type">int?</span>
    </dt>
    <dd>{{% md %}}The number of hours after initial issuing that the
certificate will become invalid.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Validity<wbr>Start<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The time after which the certificate is valid, as an
[RFC3339](https://tools.ietf.org/html/rfc3339) timestamp.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Allowed<wbr>Uses</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of keywords each describing a use that is permitted
for the issued certificate. The valid keywords are listed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Cert<wbr>Pem</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The certificate data in PEM format.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Dns<wbr>Names</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of DNS names for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Early<wbr>Renewal<wbr>Hours</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}Number of hours before the certificates expiry when a new certificate will be generated
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ip<wbr>Addresses</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of IP addresses for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Is<wbr>Ca<wbr>Certificate</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}Boolean controlling whether the CA flag will be set in the
generated certificate. Defaults to `false`, meaning that the certificate does not represent
a certificate authority.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Key<wbr>Algorithm</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The name of the algorithm for the key provided
in `private_key_pem`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Private<wbr>Key<wbr>Pem</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}PEM-encoded private key that the certificate will belong to
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Ready<wbr>For<wbr>Renewal</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Set<wbr>Subject<wbr>Key<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">*bool</span>
    </dt>
    <dd>{{% md %}}If `true`, the certificate will include
the subject key identifier. Defaults to `false`, in which case the subject
key identifier is not set at all.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Subjects</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#selfsignedcertsubject">[]Self<wbr>Signed<wbr>Cert<wbr>Subject</a></span>
    </dt>
    <dd>{{% md %}}The subject for which a certificate is being requested.
This is a nested configuration block whose structure matches the
corresponding block for `tls..CertRequest`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Uris</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}List of URIs for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Validity<wbr>End<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The time until which the certificate is invalid, as an
[RFC3339](https://tools.ietf.org/html/rfc3339) timestamp.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Validity<wbr>Period<wbr>Hours</span>
        <span class="property-indicator"></span>
        <span class="property-type">*int</span>
    </dt>
    <dd>{{% md %}}The number of hours after initial issuing that the
certificate will become invalid.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Validity<wbr>Start<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}The time after which the certificate is valid, as an
[RFC3339](https://tools.ietf.org/html/rfc3339) timestamp.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>allowed<wbr>Uses</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of keywords each describing a use that is permitted
for the issued certificate. The valid keywords are listed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>cert<wbr>Pem</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The certificate data in PEM format.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>dns<wbr>Names</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of DNS names for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>early<wbr>Renewal<wbr>Hours</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}Number of hours before the certificates expiry when a new certificate will be generated
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ip<wbr>Addresses</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of IP addresses for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>is<wbr>Ca<wbr>Certificate</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}Boolean controlling whether the CA flag will be set in the
generated certificate. Defaults to `false`, meaning that the certificate does not represent
a certificate authority.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>key<wbr>Algorithm</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The name of the algorithm for the key provided
in `private_key_pem`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>private<wbr>Key<wbr>Pem</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}PEM-encoded private key that the certificate will belong to
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ready<wbr>For<wbr>Renewal</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>set<wbr>Subject<wbr>Key<wbr>Id</span>
        <span class="property-indicator"></span>
        <span class="property-type">boolean?</span>
    </dt>
    <dd>{{% md %}}If `true`, the certificate will include
the subject key identifier. Defaults to `false`, in which case the subject
key identifier is not set at all.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>subjects</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#selfsignedcertsubject">Self<wbr>Signed<wbr>Cert<wbr>Subject[]?</a></span>
    </dt>
    <dd>{{% md %}}The subject for which a certificate is being requested.
This is a nested configuration block whose structure matches the
corresponding block for `tls..CertRequest`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>uris</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}List of URIs for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>validity<wbr>End<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The time until which the certificate is invalid, as an
[RFC3339](https://tools.ietf.org/html/rfc3339) timestamp.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>validity<wbr>Period<wbr>Hours</span>
        <span class="property-indicator"></span>
        <span class="property-type">number?</span>
    </dt>
    <dd>{{% md %}}The number of hours after initial issuing that the
certificate will become invalid.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>validity<wbr>Start<wbr>Time</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}The time after which the certificate is valid, as an
[RFC3339](https://tools.ietf.org/html/rfc3339) timestamp.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>allowed_<wbr>uses</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of keywords each describing a use that is permitted
for the issued certificate. The valid keywords are listed below.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>cert_<wbr>pem</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The certificate data in PEM format.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>dns_<wbr>names</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of DNS names for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>early_<wbr>renewal_<wbr>hours</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}Number of hours before the certificates expiry when a new certificate will be generated
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ip_<wbr>addresses</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of IP addresses for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>is_<wbr>ca_<wbr>certificate</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}Boolean controlling whether the CA flag will be set in the
generated certificate. Defaults to `false`, meaning that the certificate does not represent
a certificate authority.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>key_<wbr>algorithm</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The name of the algorithm for the key provided
in `private_key_pem`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>private_<wbr>key_<wbr>pem</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}PEM-encoded private key that the certificate will belong to
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>ready_<wbr>for_<wbr>renewal</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>set_<wbr>subject_<wbr>key_<wbr>id</span>
        <span class="property-indicator"></span>
        <span class="property-type">bool</span>
    </dt>
    <dd>{{% md %}}If `true`, the certificate will include
the subject key identifier. Defaults to `false`, in which case the subject
key identifier is not set at all.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>subjects</span>
        <span class="property-indicator"></span>
        <span class="property-type"><a href="#selfsignedcertsubject">List[Self<wbr>Signed<wbr>Cert<wbr>Subject]</a></span>
    </dt>
    <dd>{{% md %}}The subject for which a certificate is being requested.
This is a nested configuration block whose structure matches the
corresponding block for `tls..CertRequest`.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>uris</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}List of URIs for which a certificate is being requested.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>validity_<wbr>end_<wbr>time</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The time until which the certificate is invalid, as an
[RFC3339](https://tools.ietf.org/html/rfc3339) timestamp.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>validity_<wbr>period_<wbr>hours</span>
        <span class="property-indicator"></span>
        <span class="property-type">float</span>
    </dt>
    <dd>{{% md %}}The number of hours after initial issuing that the
certificate will become invalid.
{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>validity_<wbr>start_<wbr>time</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}The time after which the certificate is valid, as an
[RFC3339](https://tools.ietf.org/html/rfc3339) timestamp.
{{% /md %}}</dd>

</dl>
{{% /choosable %}}










## Supporting Types

<h4>Self<wbr>Signed<wbr>Cert<wbr>Subject</h4>
{{% choosable language nodejs %}}
> See the <a href="/docs/reference/pkg/nodejs/pulumi/tls/types/input/#SelfSignedCertSubject">input</a> and <a href="/docs/reference/pkg/nodejs/pulumi/tls/types/output/#SelfSignedCertSubject">output</a> API doc for this type.
{{% /choosable %}}

{{% choosable language go %}}
> See the <a href="https://pkg.go.dev/github.com/pulumi/pulumi-tls/sdk/go/tls/?tab=doc#SelfSignedCertSubjectArgs">input</a> and <a href="https://pkg.go.dev/github.com/pulumi/pulumi-tls/sdk/go/tls/?tab=doc#SelfSignedCertSubjectOutput">output</a> API doc for this type.
{{% /choosable %}}




{{% choosable language csharp %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Common<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Country</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Locality</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Organization</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Organizational<wbr>Unit</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Postal<wbr>Code</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Province</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Serial<wbr>Number</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Street<wbr>Addresses</span>
        <span class="property-indicator"></span>
        <span class="property-type">List<string>?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language go %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>Common<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Country</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Locality</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Organization</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Organizational<wbr>Unit</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Postal<wbr>Code</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Province</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Serial<wbr>Number</span>
        <span class="property-indicator"></span>
        <span class="property-type">*string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>Street<wbr>Addresses</span>
        <span class="property-indicator"></span>
        <span class="property-type">[]string</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language nodejs %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>common<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>country</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>locality</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>organization</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>organizational<wbr>Unit</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>postal<wbr>Code</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>province</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>serial<wbr>Number</span>
        <span class="property-indicator"></span>
        <span class="property-type">string?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>street<wbr>Addresses</span>
        <span class="property-indicator"></span>
        <span class="property-type">string[]?</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}


{{% choosable language python %}}
<dl class="resources-properties">

    <dt class="property-optional"
            title="Optional">
        <span>common<wbr>Name</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>country</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>locality</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>organization</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>organizational<wbr>Unit</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>postal<wbr>Code</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>province</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>serial<wbr>Number</span>
        <span class="property-indicator"></span>
        <span class="property-type">str</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

    <dt class="property-optional"
            title="Optional">
        <span>street<wbr>Addresses</span>
        <span class="property-indicator"></span>
        <span class="property-type">List[str]</span>
    </dt>
    <dd>{{% md %}}{{% /md %}}</dd>

</dl>
{{% /choosable %}}









<h3>Package Details</h3>
<dl class="package-details">
	<dt>Repository</dt>
	<dd><a href="https://github.com/pulumi/pulumi-tls">https://github.com/pulumi/pulumi-tls</a></dd>
	<dt>License</dt>
	<dd>Apache-2.0</dd>
    
</dl>
