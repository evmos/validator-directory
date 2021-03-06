# validator-directory

## Motivation

The Validator Directory on the Evmos Network is a place for validators to share more insights to current and future delegators. This repo will be used on Evmos.org to help create an environment where stakers can choose a validator based on a wide gamut of inputs, e.g., contribution to the Evmos ecosystem. We hope to leverage the dataset here to improve our decentralization efforts. The base template provided by the Cosmos SDK has not been sufficient to quantitatively describe a validator. It is certainly advantageous for every validator to provide as much information as he/she/they can. If there are any fields that you feel we are missing, please do not hesitate to reach out and we will do our best to accommodate. Additionally, we plan to leverage the data from: [Eco-stake Validator Profile](https://github.com/eco-stake/validator-registry) to further enrich our restaking features.

## Getting Started

1. Go to your terminal and query for your validator details. You can do this also on our website [here](https://api.evmos.org) and interact with the `/cosmos/staking/v1beta1/validators/{validator_addr}`.
2. Copy the result over to your own editor and add/edit the fields listed below. In the end, the result should be similar to the `template.example.json`.
3. Please ensure to add all the required details for each fields. If you have restaking feature enabled, please insure you add the required details on the [Eco-stake Validator Registry](https://github.com/eco-stake/validator-registry) and make a PR request on there as well. We will look up your details via the moniker and address.
4. Make a PR request on Evmos Validator Directory.

## Acceptable Fields

Please note that all fields are under `description`. If any fields are not described in the acceptable fields, we cannot accept the PR. Additionally, if you list more than 2 items in any arrays, we will show the first two. An asterisk by the type represents a required type. We encourage validators to fill out the `details` field with a bit more about themselves. However, we encourage short, succinct responses.

```
SocialEntity : {
  "name": string*,
  "link": string*,
}
```

```
Collaborator: { // One can always add more collaborators
  "identifier": string*,
  "relationship" string,
    "pubKey": {
      "@ype": "/cosmos.crypto.ed25519.PubKey",
      "key": string
    }
}
```

```
Community: {
  "involvementType": enum* // "Github | Community",
    "date_from": string* //"Feb 22, 2021",
    "date_to": string //"Present",
    "handle": string,
    "description": string,
    "contribution": [{
      "features": { // as Github
        "name": string*,
        "sha": string,
        "repo": string, // link/branch link
        "description": string,
      },
      { //Community
        "name": string*,
        "description": string
      }
    }]
}
```

```
Infrastructure: {
  "hosting_provider": string,
  "stack_details": string
  }
```

- `social: SocialEntity[]`
- `collaborators: Collaborator[]`
- `communities: Community[]`
- `infrastructures: Infrastructure[]` - there is no way for Evmos to validate these stack details however, we encourage our validators to be as descriptive as they can,
- `offers_auto_compounding: boolean` - default is false. If true, we will leverage the data on [here](https://github.com/eco-stake/validator-registry) which generates the h json data [here](https://validators.cosmos.directory/chains/evmos).
- `relayers: boolean` - default is false
- `is_recent: boolean` - if the validator is formed in the last 3 months, it will be a true
- `has_liquid_staking: boolean` - default is false
- `has_interchain_account: boolean` - default is false
