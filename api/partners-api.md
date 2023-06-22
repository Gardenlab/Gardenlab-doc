---
description: Description of the API that can be used by partners to update the NFT
---

# Partners API

## Introduction

A partner API is being developed and allows third party to trigger actions in a NFT collection on Gardenlab.&#x20;

For now, the API allows partners to trigger NFT creation and reservation for later claim by the user. The claim shall be performed by the user, after logging in with its email. It also allows to consume an interaction on a NFT, designated by the owner's email address. The interaction shall be created and configured beforehand on the collection admin tool.

An API key and a configured collection are required to perform properly those actions.

## Description

{% swagger src="../.gitbook/assets/openAPI_spec.yml" path="/newUserForPartner" method="post" %}
[openAPI_spec.yml](../.gitbook/assets/openAPI_spec.yml)
{% endswagger %}

{% swagger src="../.gitbook/assets/openAPI_spec.yml" path="/newActionForUser" method="post" %}
[openAPI_spec.yml](../.gitbook/assets/openAPI_spec.yml)
{% endswagger %}

{% swagger src="../.gitbook/assets/openAPI_spec (2).yml" path="/getNftByTokenId" method="get" %}
[openAPI_spec (2).yml](<../.gitbook/assets/openAPI_spec (2).yml>)
{% endswagger %}
