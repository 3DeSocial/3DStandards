
# H1 3D NFT Specification 


## H2 Overview

This document specifies how we can use the existing properties of the DeSo API objects to store the data requried for a 3D NFT.

Table Columns

Label: Friendly name for field
Field Name: The name of the JSON property to use will be used
Source Object: The name of the DeSo Object / Datatype which contains the field
Data Type: Type of data that can be stored
Content: Description or example of content
JSON Property: JSON element name for nested data
JSON Property: JSON nested data


| **Label**              | **Field Name**               | **Source Object** | **Data Type** | ** JSON Property Name **                                                        | ** JSON Element Content **                   |
|------------------------|------------------------------|-------------------|---------------|--------------------------------------------------------------------|----------------------------|
| On Sale                | IsForSale                    | NFT Entry         | bool          |                                                                    |                            |
| Copies                 | NumNFTCopies                 | NFT Entry         | int           |                                                                    |                            |
| Model URL              | EncryptedUnlockableText      | NFT Entry         | string/json   | Asset Storage URL linking to downloadable zip on ARWeave, IPFS etc |                            |
| Minimum Bid            | LowestBidAmountNanos         | NFT Entry         | int           |                                                                    |                            |
| Description            | Body                         | Post Entry          | text          |                                                                    |                            |
| Preview Images or Gifs | ImageURLs                    | Post Entry          | array/string  |                                                                    |                            |
| Preview Videos         | VideoURLs                    | Post Entry          | array/string  |                                                                    |                            |
| Hide From Feeds        | IsHidden                     | Post Entry          | bool          |                                                                    |                            |
| Model Category         | PostExtraData => 3DExtraData | Post Entry          | string        | Examples: item/scenery/avatar/scene/other                                    |                            |
| Model Formats          | PostExtraData => 3DExtraData | Post Entry          | string/json   | [&lt;format_name&gt;] =>                                                      | high_poly_foldername       |
|                        |                              |                   |               |                                                                    | low_poly_foldername        |
|                        |                              |                   |               | [&lt;format_name&gt;] =>                                                      | high_poly_foldername       |
|                        |                              |                   |               |                                                                    | low_poly_foldername        |
| Asset Licences         | PostExtraData => 3DExtraData | NFT Post          | string/json   | [&lt;format_name&gt;] =>                                                      | high_poly_lisence_filename |
|                        |                              |                   |               |                                                                    | low_poly_licence_filename  |
|                        |                              |                   |               |                                                                    |                            |
