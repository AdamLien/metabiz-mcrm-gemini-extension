# metabiz mCRM for Gemini CLI

Connect Gemini CLI to [metabiz mCRM](https://metabiz.ai/products/mcrm/chatgpt), the customer relationship management platform by metabiz Co., Ltd. 用益網路科技股份有限公司.

This repository contains public client configuration only. The hosted MCP service and CRM remain operated by metabiz.

**繁體中文：**透過 Gemini CLI 使用 metabiz mCRM，查詢已授權商家的會員、標籤、維度與分眾，並建立可審查的會員經營提案。適合零售、餐飲及服務品牌；[了解產品與預約諮詢](https://metabiz.ai/contact)。

## Customer insights and engagement

metabiz helps retail, restaurant and service businesses connect member management, segmentation and customer engagement. Use your existing mCRM account and merchant permissions to access the tools made available by the MCP service.

- Look up authorized member data, tags, dimensions and saved segments.
- Prepare member summaries and customer engagement proposals.
- Review a proposed change or message in metabiz before explicitly executing it through MCP. Staging alone does not write or send.

[Explore metabiz](https://metabiz.ai/) · [Book a consultation](https://metabiz.ai/contact) · [Product documentation](https://metabiz.ai/products/mcrm/chatgpt)

## Install

Install [Gemini CLI](https://geminicli.com/docs/get-started/installation/), then run:

```sh
gemini extensions install https://github.com/AdamLien/metabiz-mcrm-gemini-extension
```

Start `gemini`. When prompted to authenticate, or using `/mcp auth metabiz-mcrm`, complete the metabiz browser login, choose your merchant and approve the `mcrm` scope. Use `/mcp` to check connection status and available tools. OAuth credentials are managed locally by Gemini CLI; this package has no embedded passwords, tokens or API keys.

Requires an existing metabiz mCRM account with access enabled for your merchant. Installing the extension does not provision a CRM subscription or bypass account permissions. Contact [metabiz](https://metabiz.ai/contact) for onboarding and availability in Taiwan.

Authentication uses the local browser callback `http://localhost:18539/oauth/callback`. Keep this local port available during login; it must not be forwarded to an external host. The callback must be approved in the metabiz MCP service configuration before this extension can authenticate.

## Try it

Start with read-only requests against your authorized merchant:

```text
Check my current metabiz mCRM authorization and merchant context.
List the tags and dimensions available in this merchant.
List my saved member segments and explain their criteria.
```

For writes, first request a proposal. Review the exact merchant, recipients and content at the returned metabiz review URL as the same operator. Approve only the intended operation, then request explicit execution. Never send test messages to real recipients without authorization.

## Data and support

Gemini CLI exchanges authorized tool requests with the hosted production endpoint `https://mcrm-mcp.metabiz.tw/mcp`. Returned CRM information enters the AI client context. Review your organization's data-sharing requirements and Google's applicable Gemini CLI terms before connecting.

- [metabiz service privacy information](https://metabiz.ai/products/mcrm/chatgpt/privacy)
- [Support and consultation](https://metabiz.ai/contact) or metabiz@metabiz.tw
- [Gemini CLI terms and privacy](https://geminicli.com/docs/tos-privacy/)

The linked product pages currently use ChatGPT-oriented wording. This independent Gemini CLI integration uses the same metabiz MCP service; it does not imply Google endorsement or directory approval. Available tools depend on the server release and account permissions. Full live acceptance of every tool, including message delivery and App push, is not claimed by this package.

## Development and public discovery

Validate the package with `gemini extensions validate .`, then install the local directory for testing. Branch flow: feature → develop for validation; the same feature → main for public releases.

The [official gallery crawler](https://geminicli.com/docs/extensions/releasing/) discovers public repositories tagged `gemini-cli-extension` with a root-level `gemini-extension.json`. Publishing this repository makes it eligible for discovery; it does not prove that the gallery has listed it. The MIT license covers this client package, not access to the hosted metabiz service or customer data.
