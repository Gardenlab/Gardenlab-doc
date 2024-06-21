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

Swagger demo API : [https://api-docs-demo.gardenlab.io/](https://api-docs-demo.gardenlab.io/)&#x20;

## Description

### Configuration

#### Interactions

{% swagger src="../.gitbook/assets/Partner_API.yaml" path="/saveActionInteraction" method="post" %}
[Partner_API.yaml](../.gitbook/assets/Partner_API.yaml)
{% endswagger %}

### Operation

#### User creation

{% swagger src="../.gitbook/assets/Partner_API (4).yaml" path="/newUserForPartner" method="post" %}
[Partner_API (4).yaml](<../.gitbook/assets/Partner_API (4).yaml>)
{% endswagger %}

**Note**: When creating a NFT for a user, this NFT is prepared but not minted. The mint of the NFT occurs when the user claims it using the email address.

#### Action

{% swagger src="../.gitbook/assets/Partner_API.yaml" path="/newActionForUser" method="post" %}
[Partner_API.yaml](../.gitbook/assets/Partner_API.yaml)
{% endswagger %}

**Note**: The action saved for a NFT is applied if the NFT is minted or not.

#### Mint token

{% swagger src="../.gitbook/assets/Partner_API (4).yaml" path="/mintTokenForUser" method="post" %}
[Partner_API (4).yaml](<../.gitbook/assets/Partner_API (4).yaml>)
{% endswagger %}

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

{% swagger src="../.gitbook/assets/Partner_API (2).yaml" path="/getBlockchainTxForToken" method="get" %}
[Partner_API (2).yaml](<../.gitbook/assets/Partner_API (2).yaml>)
{% endswagger %}



## Webhooks

It is also possible to set up webhooks to get notified about some specific events occuring in Gardenlab.

The failure object is sent only when there is no "hope" about succeeding in performing the blockchain transactions. Gardenlab system is designed to try multiple times to perform a transaction if no fatal error occurs on the transaction.

### New interaction with blockchain update:

#### Type :&#x20;

```typescript
newBcInteraction
```

#### Header:

```typescript
"X-API-key": string // The API key configured by the partner
```

#### Success Content:

```javascript
{
    sucess: true,
    contract: string, // The contract address
    tokenId: string, // The token ID
    actionType: string, // The webhook/action type (newBcInteraction)
    actionAtInSeconds: string, // The date of the action in seconds
    at: {"_seconds": number, "_nanoseconds": number}, // The date in an object
    transactionUrl: string, // The blockchain explorer page for this transaction
    txHash: string, // The blockchain transaction hash
    newUri: string, // The new URI of the token
}
```

#### &#x20;Failure Content:

```javascript
{
    sucess: false,
    error: string,
    contract: string, // The contract address
    tokenId: string, // The token ID
    actionType: string, // The webhook/action type (newBcInteraction)
    actionAtInSeconds: string, // The date of the action in seconds
    at: {"_seconds": number, "_nanoseconds": number}, // The date in an object
}
```

###

### New NFT minted

#### Type :&#x20;

```typescript
newBcNftMint
```

#### Header:

```typescript
"X-API-key": string // The API key configured by the partner
```

#### Success content:

```javascript
{
    success: true,
    contract: string, // The contract address
    tokenId: string, // The token ID
    actionType: string, // The webhook/action type (newBcNftMint)
    at: {"_seconds": number, "_nanoseconds": number}, // The date in an object
    transactionUrl: string, // The blockchain explorer page for this transaction
    txHash: string, // The blockchain transaction hash
}
```

#### Failure content:

```javascript
{
    success: false,
    error: string, // The error message
    contract: string, // The contract address
    tokenId: string, // The token ID
    actionType: string, // The webhook/action type (newBcNftMint)
    at: {"_seconds": number, "_nanoseconds": number}, // The date in an object
}
```
