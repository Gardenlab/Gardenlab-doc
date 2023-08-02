---
description: Description of the API that can be used by partners to update the NFT
cover: >-
  https://images.unsplash.com/photo-1534224039826-c7a0eda0e6b3?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHwyfHxjb25uZWN0aW9ufGVufDB8fHx8MTY4ODIzODgxOHww&ixlib=rb-4.0.3&q=85
coverY: 0
---

# Partners API

## Introduction

A partner API is being developed and allows third party to trigger actions in a NFT collection on Gardenlab.&#x20;

For now, the API allows partners to trigger NFT creation and reservation for later claim by the user. The claim shall be performed by the user, after logging in with its email. It also allows to consume an interaction on a NFT, designated by the owner's email address. The interaction shall be created and configured beforehand on the collection admin tool.

An API key and a configured collection are required to properly perform those actions.

## Description

### Configuration

#### Interactions

{% swagger src="../.gitbook/assets/Partner_API.yaml" path="/saveActionInteraction" method="post" %}
[Partner_API.yaml](../.gitbook/assets/Partner_API.yaml)
{% endswagger %}

### Operation

#### User creation

{% swagger src="../.gitbook/assets/Partner_API.yaml" path="/newUserForPartner" method="post" %}
[Partner_API.yaml](../.gitbook/assets/Partner_API.yaml)
{% endswagger %}

**Note**: When creating a NFT for a user, this NFT is prepared but not minted. The mint of the NFT occurs when the user claims it using the email address.

#### Action

{% swagger src="../.gitbook/assets/Partner_API.yaml" path="/newActionForUser" method="post" %}
[Partner_API.yaml](../.gitbook/assets/Partner_API.yaml)
{% endswagger %}

**Note**: The action saved for a NFT is applied if the NFT is minted or not.

### Getters

{% swagger src="../.gitbook/assets/Partner_API.yaml" path="/getNftByTokenId" method="get" %}
[Partner_API.yaml](../.gitbook/assets/Partner_API.yaml)
{% endswagger %}

{% swagger src="../.gitbook/assets/Partner_API.yaml" path="/getAllInteractions" method="get" %}
[Partner_API.yaml](../.gitbook/assets/Partner_API.yaml)
{% endswagger %}

{% swagger src="../.gitbook/assets/Partner_API.yaml" path="/getAllInteractionScansForToken" method="get" %}
[Partner_API.yaml](../.gitbook/assets/Partner_API.yaml)
{% endswagger %}
