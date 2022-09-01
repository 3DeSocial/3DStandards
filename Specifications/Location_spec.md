
# Location Specification 

## Overview

This document outlines an approach for storing the information required to render a virtual location.

When browing the web, a browser downloads and HTML file describing a web page.

An older technology VRML was created over a decade ago to describe VR environments in the same way.

Today we can use JSON to describe locations and use the blockchain to store, index, discover those environments.

### JSON Example


```

spaceConfig: [{scenery:<NFTHash>,  // NFT hash for 3D NFTs of scenery
                items: [NFTHash, NFTHash, NFTHash, NFTHash, NFTHash, NFTHash],
                background: <path to skybox> OR NFTHash for skybox minted as NFT,
                walkSpeed: 10,
                sceneScale: 0.01,
                scaleModelToHeight:2, // Default size for NFTs displayed in room
                scaleModelToWidth: 2,
                scaleModelToDepth: 2,   
                playerStartPos: {x:0,y:4,z:0},  // location in the environment where the player will appear
                avatarSize: {width: 1, height:1, depth:1}, // Max dimensions of avatar
                firstPerson: true,  // Default perspective on entering
                vrType:vrControls // default control method in VR]
```
