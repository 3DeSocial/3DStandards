
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
| Asset URLS              | PostExtraData.3DExtraData.3DModels[] | Post Entry         | string/json array  | JSON array of 3DModel JSON objects linking to downloadable zips on ARWeave, IPFS etc |                            |



### 3DModel Example

The 3DModels[] property of 3D extra data is an array of 3DModel json objects.

In the example below the 3DModel assets are stored in two different formats - gtlf and threejsscene

in ModelFormats the array values low_poly_version and high_polyversion are the **folder names** within the uploaded zip file in which the assets can be found within the zip file

in ModelLicenses the array values low_poly_version_licence and high_polyversion_licence are the **file names** within the uploaded zip file of the licence for each format and version of the file.

A single 3DModel is formatted as follows:

```

{
	ModelUrl: 'https://arweave.org/arweaveurl1',
	ModelCats: ['item'],
	ModelFormats: {
		'gtlf':['low_poly_version','high_polyversion'],
		'threejsscene':['hd_version','low_poly_version'],
	ModelLicenses: {
		'gtlf':['low_poly_version_licence','high_polyversion_licence'],
		'threejsscene':['hd_version_licence','low_poly_version_licence']
	}
}
```
### 3DExtraData Example

3DExtraData is a JSON object stored as a property of PostExtraData
Most 3D NFTs will be a single model, but to facilitate item collections we can use an array of models

```
{
	
	Models:[3DModel,3DModel]
		
}
```

Expanded 3DExtraData example showing an NFT representing 2 3D object (for example this could be a furniture set with a table and a chair, or a clothing set with a top and bottom half): 

```
{
	Models:[{
			ModelUrl: 'https://arweave.org/arweaveurl1',
			ModelCats: ['item'],
			ModelFormats: {
				'gtlf':['low_poly_version','high_polyversion'],
				'threejsscene':['hd_version','low_poly_version'],
			ModelLicenses: {
				'gtlf':['low_poly_version_licence','high_polyversion_licence'],
				'threejsscene':['hd_version_licence','low_poly_version_licence']
			}
		},{
			ModelUrl'https://arweave.org/arweaveurl2',
			ModelCats: ['item'],
			ModelFormats: {
				'gtlf':['low_poly_version','high_polyversion'],
				'threejsscene':['hd_version','low_poly_version'],
			ModelLicenses: {
				'gtlf':['low_poly_version_licence','high_polyversion_licence'],
				'threejsscene':['hd_version_licence','low_poly_version_licence']
			}
		}]		
}
```
### Asset Storage

It is recommended that assets should be stored on permanent decentralized storage such as ARWeave or IPFS to maximize the value of the asset.

Asset files can be stored in a zip file with the folders below to ensure that consumers of the NFT (i.e. metaverse platforms, digital galleries, marketplaces) will can easily find the version of the files needed for their software.


| Asset Format Folder Name | Asset Version Folder Name | Files                  |
|--------------------------|-----------------------------|------------------------|
| < format_name_1 >  | < version_name_1 >     | < asset_file >   |
|                          |                             | < asset_file >   |
| Example                  |                             |                        |
| gtlf                     | high_poly_version           | high_polyasset_file.gtlf        |
|                          |                             | high_polyasset_file.bin         |
|                          |                             | high_polyasset_file_lisence.txt |
|                          | low_poly_version            | low_poly_asset_file.gtlf        |
|                          |                             | low_poly_asset_file.bin         |
|                          |                             | low_poly_asset_file_lisence.txt |
