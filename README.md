# rn-instastory-share

Share your images to instagram stories.

| OS | Type | Supported |
|---|---|:---:|
| iOS | BASE64 | YES |
|  | FILE | YES |
| Android | BASE64 | YES |
|  | FILE | NO |

## Getting started

`$ npm install rn-instastory-share --save`

## Installation

`$ react-native link react-native-story-share`

### iOS

#### Info.plist

+ add `instagram-stories` and `snapchat` to the `LSApplicationQueriesSchemes` key in your app's Info.plist.

```diff
...
<key>LSApplicationQueriesSchemes</key>
<array>
	...
+	<string>instagram-stories</string>
</array>
...
```

`$ cd ios`

`$ pod install`

## Usage

### Share To Instagram
```javascript
import RNStoryShare from "rn-instastory-share";

RNStoryShare.isInstagramAvailable()
  .then(isAvailable => {

    if(isAvailable){
      RNStoryShare.shareToInstagram({
        type: RNStoryShare.BASE64, // or RNStoryShare.FILE
        attributionLink: 'https://myproject.com',
        backgroundAsset: 'data:image/png;base64,iVBO...',
        stickerAsset: 'data:image/png;base64,iVBO...',
        backgroundBottomColor: '#f44162',
        backgroundTopColor: '#f4a142'
      });
    }
  })
  .catch(e => console.log(e));
```

## API

### Constants

| Name | Value |
|---|---|
| BASE64 | "base64" |
| FILE | "file" |

### Methods

#### `isInstagramAvailable(): Promise<boolean>`
Return a boolean indicating if Instagram is available on the phone.

#### `shareToInstagram(config: ShareConfigObject): Promise<void>`
```
type ShareConfigObject = {
  type: "base64" || "file",
	attributionLink: string,
	backgroundAsset: string,
	stickerAsset: string,
	stickerOptions: {
		height: integer,
		width: integer
	}
}
```
Shares a file or base64 image as background, sticker or both to Instagram. The background colors are only applyed when no background asset is set.