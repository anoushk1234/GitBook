---
description: >-
  Shadow Drive exposes an API that you can interact directly without the need of
  the CLI or SDK. You may build on top of these methods.
---

# Shadow Drive API

Mainnet-Beta API Base URL: https://shadow-storage.genesysgo.net

<details>

<summary>POST /storage-account - Creates a new storage account</summary>

Request content type: application/json

Parameters:

1. transaction: Serialized create storage account transaction that's partially signed by the storage account owner

Response:

```json
{
    "shdw_bucket": String,
    "transaction_signature": String
}
```

</details>

<details>

<summary>POST /upload - Uploads a single file</summary>

Request content type: multipart/form-data

Parameters (FormData fields):

1. file: The file you want to upload
2. transaction: Serialized store file transaction that's partially signed by a storage account owner or admin

Response:

```json
{
    "finalized_location": String,
    "transaction_signature": String
}
```

</details>

<details>

<summary>POST /upload-batch - Uploads multiple files at once</summary>

Request content type: multipart/form-data

Parameters (FormData fields):

1. file: You may add up to 5 files each with a field name of "file".
2. transaction: Serialized transaction with each store file instruction corresponding to the files supplied that's partially signed by a storage account owner or admin

Response:

```
{
    "finalized_locations": [String]
    "transaction_signature": String
}
```

</details>

<details>

<summary>POST /edit - Edits an existing file</summary>

Request content type: multipart/form-data

Parameters (FormData fields):

1. file: Data of the file you want to replace the file you're requesting to edit
2. transaction: Serialized edit file transaction that's partially signed by a storage account owner or admin

Response:

```
{
    "finalized_location": String,
    "transaction_signature": String
}
```

</details>

<details>

<summary>POST /list-objects - Get a list of all files associated with a storage account</summary>

Request content type: application/json

Parameters:

1. storageAccount: String version of the storage account PublicKey that you want to get a list of files for

Response:

```
{
    "keys": [String]
}
```

</details>
