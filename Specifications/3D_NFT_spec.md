
# 3D NFT Specification 


## Overview

This document specifies how we can use the existing properties of the DeSo API objects to store the data requried for a 3D NFT and a suggested format for asset and licence file storage.

New properties can be stored in 3DExtraData which would be a property of PostExtraData

Blochain Data Reference: <https://docs.deso.org/backend/blockchain-data/basics/data-types>

Note that traits are not included as they are not a requirement for 3D NFTs so are aout of scope for this document.

### On-Chain Storage

Label: Friendly name for field

Field Name: The name of the JSON property to use will be used

Source Object: The name of the DeSo Object / Datatype which contains the field

Data Type: Type of data that can be stored

Content: Description or example of content

JSON Property: JSON element name for nested data

JSON Property: JSON nested data


| **Label**              | **Field Name**               | **Source Object** | **Data Type** | **JSON Property Name**                                                        | **JSON Element Content**                   |
|------------------------|------------------------------|-------------------|---------------|--------------------------------------------------------------------|----------------------------|
| On Sale                | IsForSale                    | NFT Entry         | bool          |                                                                    |                            |
| Copies                 | NumNFTCopies                 | NFT Entry         | int           |                                                                    |                            |
| Minimum Bid            | LowestBidAmountNanos         | NFT Entry         | int           |                                                                    |                            |
| Description            | Body                         | Post Entry          | text          |                                                                    |                            |
| Preview Images or Gifs | ImageURLs                    | Post Entry          | array/string  |                                                                    |                            |
| Preview Videos         | VideoURLs                    | Post Entry          | array/string  |                                                                    |                            |
| Hide From Feeds        | IsHidden                     | Post Entry          | bool          |                                                                    |                            |
| Asset URLS              | PostExtraData.3DExtraData.AssetURLS | Post Entry         | string/json array  | JSON array of URLs linking to downloadable zip on ARWeave, IPFS etc |                            |
| Model Category         | PostExtraData.3DExtraData.ModelCat | Post Entry          | string        | Examples: item/scenery/avatar/scene/other                                    |                            |
| Model Formats          | PostExtraData.3DExtraData.ModelFormat | Post Entry          | string/json   | [&lt;format_name&gt;] =>                                                      | high_poly_foldername       |
|                        |                              |                   |               |                                                                    | low_poly_foldername        |
|                        |                              |                   |               | [&lt;format_name&gt;] =>                                                      | high_poly_foldername       |
|                        |                              |                   |               |                                                                    | low_poly_foldername        |
| Asset Licences         | PostExtraData.3DExtraData.ModelLicence | Post Entry         | string/json   | [&lt;format_name&gt;] =>                                                      | high_poly_licence_filename |
|                        |                              |                   |               |                                                                    | low_poly_licence_filename  |
|                        |                              |                   |               |                                                                    |                            |


### Asset Storage

It is recommended that assets should be stored on permanent decentralized storage such as ARWeave or IPFS to maximize the value of the asset.

Asset files can be stored in a zip file with the folders below to ensure that consumers of the NFT (i.e. metaverse platforms, digital galleries, marketplaces) will can easily find the version of the files needed for their software.


| Asset Format Folder Name | Asset Version Folder Name | Files                  |
|--------------------------|-----------------------------|------------------------|
| < format_name_1 >  | < version_name_1 >     | < asset_file >   |
|                          |                             | < asset_file >   |
| Example                  |                             |                        |
| gtlf                     | high_poly_version           | asset_file.gtlf        |
|                          |                             | asset_file.bin         |
|                          |                             | asset_file_lisence.txt |
|                          | low_poly_version            | asset_file.gtlf        |
|                          |                             | asset_file.bin         |
|                          |                             | asset_file_lisence.txt |
