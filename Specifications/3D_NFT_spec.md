| **Label**              | **Field Name**               | **Source Object** | **Data Type** | **Content**                                                        | **null**                   |
|------------------------|------------------------------|-------------------|---------------|--------------------------------------------------------------------|----------------------------|
| On Sale                | IsForSale                    | NFT Entry         | bool          |                                                                    |                            |
| Copies                 | NumNFTCopies                 | NFT Entry         | int           |                                                                    |                            |
| Model URL              | EncryptedUnlockableText      | NFT Entry         | string/json   | Asset Storage URL linking to downloadable zip on ARWeave, IPFS etc |                            |
| Minimum Bid            | LowestBidAmountNanos         | NFT Entry         | int           |                                                                    |                            |
|                        |                              |                   |               |                                                                    |                            |
| Description            | Body                         | NFT Post          | text          |                                                                    |                            |
| Preview Images or Gifs | ImageURLs                    | NFT Post          | array/string  |                                                                    |                            |
| Preview Videos         | VideoURLs                    | NFT Post          | array/string  |                                                                    |                            |
| Hide From Feeds        | IsHidden                     | NFT Post          | bool          |                                                                    |                            |
| Model Category         | PostExtraData => 3DExtraData | NFT Post          | string        | item/scenery/avatar/scene/other                                    |                            |
| Model Formats          | PostExtraData => 3DExtraData | NFT Post          | string/json   | [&lt;format_name&gt;] =>                                                      | high_poly_foldername       |
|                        |                              |                   |               |                                                                    | low_poly_foldername        |
|                        |                              |                   |               | [&lt;format_name&gt;] =>                                                      | high_poly_foldername       |
|                        |                              |                   |               |                                                                    | low_poly_foldername        |
| Asset Licences         | PostExtraData => 3DExtraData | NFT Post          | string/json   | [&lt;format_name&gt;] =>                                                      | high_poly_lisence_filename |
|                        |                              |                   |               |                                                                    | low_poly_licence_filename  |
|                        |                              |                   |               |                                                                    |                            |
