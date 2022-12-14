<!-- If you update the list of supported languages for CodeQL, update docs-internal/content/get-started/learning-about-github/github-language-support.md to reflect the changes. -->
- C/C++
- C#
- Go
- Java
- JavaScript/TypeScript
- Python{% ifversion fpt or ghes > 3.3 or ghec or ghae > 3.3 %}
- Ruby

{% ifversion ghes < 3.8 or ghae < 3.8 %}
{% note %}

**Note**: {% data variables.product.prodname_codeql %} analysis for Ruby is currently in beta. During the beta, analysis of Ruby will be less comprehensive than {% data variables.product.prodname_codeql %} analysis of other languages.

{% endnote %}
{% endif %}

For more information, see the documentation on the {% data variables.product.prodname_codeql %} website: "[Supported languages and frameworks](https://codeql.github.com/docs/codeql-overview/supported-languages-and-frameworks/)."
{% endif %}
