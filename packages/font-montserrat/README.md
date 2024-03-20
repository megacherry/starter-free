# Prerequisite
First install the dependencies running `yarn install`, then make sure to build the package using `yarn build` and add the package as a dependency to the package/app you want to consume it from (could be the `app` or `ui` package) like so:
```
"dependencies": {
  "@tamagui-google-fonts/montserrat": "*"
}
```
## Usage
### Expo
  
Add this to the root of your file:
    
```ts
import { useFonts } from 'expo-font'

export default function App() {
  const [loaded] = useFonts({
    MontserratThin: require('@tamagui-google-fonts/montserrat/fonts/static/Montserrat-Thin.ttf'),
    MontserratExtraLight: require('@tamagui-google-fonts/montserrat/fonts/static/Montserrat-ExtraLight.ttf'),
    MontserratLight: require('@tamagui-google-fonts/montserrat/fonts/static/Montserrat-Light.ttf'),
    Montserrat: require('@tamagui-google-fonts/montserrat/fonts/static/Montserrat-Regular.ttf'),
    MontserratMedium: require('@tamagui-google-fonts/montserrat/fonts/static/Montserrat-Medium.ttf'),
    MontserratSemiBold: require('@tamagui-google-fonts/montserrat/fonts/static/Montserrat-SemiBold.ttf'),
    MontserratBold: require('@tamagui-google-fonts/montserrat/fonts/static/Montserrat-Bold.ttf'),
    MontserratExtraBold: require('@tamagui-google-fonts/montserrat/fonts/static/Montserrat-ExtraBold.ttf'),
    MontserratBlack: require('@tamagui-google-fonts/montserrat/fonts/static/Montserrat-Black.ttf'),
    MontserratThinItalic: require('@tamagui-google-fonts/montserrat/fonts/static/Montserrat-ThinItalic.ttf'),
    MontserratExtraLightItalic: require('@tamagui-google-fonts/montserrat/fonts/static/Montserrat-ExtraLightItalic.ttf'),
    MontserratLightItalic: require('@tamagui-google-fonts/montserrat/fonts/static/Montserrat-LightItalic.ttf'),
    MontserratItalic: require('@tamagui-google-fonts/montserrat/fonts/static/Montserrat-Italic.ttf'),
    MontserratMediumItalic: require('@tamagui-google-fonts/montserrat/fonts/static/Montserrat-MediumItalic.ttf'),
    MontserratSemiBoldItalic: require('@tamagui-google-fonts/montserrat/fonts/static/Montserrat-SemiBoldItalic.ttf'),
    MontserratBoldItalic: require('@tamagui-google-fonts/montserrat/fonts/static/Montserrat-BoldItalic.ttf'),
    MontserratExtraBoldItalic: require('@tamagui-google-fonts/montserrat/fonts/static/Montserrat-ExtraBoldItalic.ttf'),
    MontserratBlackItalic: require('@tamagui-google-fonts/montserrat/fonts/static/Montserrat-BlackItalic.ttf'),
  })
// ...
```

## Web

Get the font's script (`<link>` or `@import`) and add it to `<head>` from [here](https://fonts.google.com/specimen/Montserrat)


## Next.js Font (next/font/google)

Import the font from `next/font/google` and give it a variable name in your `_app.tsx` like so:

```ts
import { Montserrat } from 'next/font/google' // the casing might differ

const font = Montserrat({
  variable: '--my-font',
})
```

Add the variable style in `_app.tsx`:

```tsx
<div className={font.variable}>
  {*/ ...rest of your _app.tsx tree */}
</div>
```

Then go to the generated font package and update `family` with the variable.

So, change it from:
```ts
return createFont({
    family: isWeb
      ? '"Montserrat", -apple-system, system-ui, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif'
      : 'Montserrat',
```

To:
```ts
return createFont({
    family: isWeb
      ? 'var(--my-font), -apple-system, system-ui, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif'
      : 'Montserrat',
```


## Usage in config

```ts
import { createMontserratFont } from '@tamagui-google-fonts/montserrat' 

export const myFont = createMontserratFont(
  {
    face: {
    "100": {
        "normal": "MontserratThin",
        "italic": "MontserratThinItalic"
    },
    "200": {
        "normal": "MontserratExtraLight",
        "italic": "MontserratExtraLightItalic"
    },
    "300": {
        "normal": "MontserratLight",
        "italic": "MontserratLightItalic"
    },
    "400": {
        "normal": "Montserrat",
        "italic": "MontserratItalic"
    },
    "500": {
        "normal": "MontserratMedium",
        "italic": "MontserratMediumItalic"
    },
    "600": {
        "normal": "MontserratSemiBold",
        "italic": "MontserratSemiBoldItalic"
    },
    "700": {
        "normal": "MontserratBold",
        "italic": "MontserratBoldItalic"
    },
    "800": {
        "normal": "MontserratExtraBold",
        "italic": "MontserratExtraBoldItalic"
    },
    "900": {
        "normal": "MontserratBlack",
        "italic": "MontserratBlackItalic"
    }
}
        },
  {
    // customize the size and line height scaling to your own needs
    // sizeSize: (size) => Math.round(size * 1.1),
    // sizeLineHeight: (size) => size + 5,
  }
)
```

NOTE: these instructions are auto-generated and might not be accurate with some fonts since not all fonts share the same conventions. you may need to edit them out to get them to work.
