# Configure design system in Tailwind

## Introduction

This guide explains how to configure a design system in Tailwind and be able to use class variables.
We will use the following design system as an example: [Figma](https://www.figma.com/file/DD4jXGrqqJn1Opgtdg7ChN/Tailwind-Design-System?node-id=902%3A25832)

**Why set up a design system?**

Setting up a design system helps improve development speed by allowing variables to be reused.
To begin with, we will mainly work on the `tailwind.config.js` file.

```
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./*.{html,js}"],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

Using `theme` vs `extend`

If you want to keep the variables that Tailwind includes by default, it is necessary to work on the `extend: {}`. For this case, we will work directly on the `theme: {}` that overwrites the Tailwind variables that we configure since we will only use styles from the design system in the code.

### VS Code extension for Tailwind

[Tailwind CSS IntelliSense](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss)

## Custom Fonts

Import the new font in the CSS file where you import tailwind classes.

```
/* Header font */
@import url('https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&display=swap');
/* Body font */
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');

@tailwind base;
@tailwind components;
@tailwind utilities;
```

Add the "fontFamily" property inside the "theme" object to include both fonts.

```
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./*.{html,js}"],
  theme: {
    fontFamily: {
      inter: 'Inter, sans-serif',
      space: 'Space Grotesk, sans-serif',
    },
    extend: {},
  },
  plugins: [],
}
```

If you already installed the VS Code extension for Tailwind, you will see the code hints.

## Typography

Add the "fontSize" property. In this property, we can add the size, the line height and if we want, we can also include the letter spacing.

```
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./*.{html,js}"],
  theme: {
    fontFamily: {
      inter: 'Inter, sans-serif',
      space: 'Space Grotesk, sans-serif',
    },
    fontSize: {
      'title-h1': ['48px', { lineHeight: '64px' }],
      'title-h2': ['40px', { lineHeight: '52px' }],
      'title-h3': ['32px', { lineHeight: '42px' }],
      'title-h4': ['24px', { lineHeight: '32px' }],
      'title-h5': ['20px', { lineHeight: '28px' }],
      'title-h6': ['16px', { lineHeight: '20px' }],
      'body-lg': ['18px', { lineHeight: '28px' }],
      'body-md': ['16px', { lineHeight: '24px' }],
      'body-sm': ['14px', { lineHeight: '20px' }],
      'body-xs': ['12px', { lineHeight: '16px' }],
    },
    extend: {},
  },
  plugins: [],
}
```

An example with letter spacing could be:

```
fontSize: {
  'title-h1': ['48px', { lineHeight: '64px', letterSpacing: '1px' }]
}
```

## Colors

If the color has no variants, it can be added as a string `'white': '#ffffff'`
If the color has variants, it can be an object where each property is a variant.

```
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./*.{html,js}"],
  theme: {
    fontFamily: {
      inter: 'Inter, sans-serif',
      space: 'Space Grotesk, sans-serif',
    },
    fontSize: {
      'title-h1': ['48px', { lineHeight: '64px' }],
      'title-h2': ['40px', { lineHeight: '52px' }],
      'title-h3': ['32px', { lineHeight: '42px' }],
      'title-h4': ['24px', { lineHeight: '32px' }],
      'title-h5': ['20px', { lineHeight: '28px' }],
      'title-h6': ['16px', { lineHeight: '20px' }],
      'body-lg': ['18px', { lineHeight: '28px' }],
      'body-md': ['16px', { lineHeight: '24px' }],
      'body-sm': ['14px', { lineHeight: '20px' }],
      'body-xs': ['12px', { lineHeight: '16px' }],
    },
    colors: {
      transparent: 'transparent',
      current: 'currentColor',
      white: '#ffffff',
      black: '#000000',
      primary: {
        50: '#F3F3FC',
        100: '#DEDFF7',
        200: '#C9CCF3',
        300: '#ACB0EC',
        400: '#7279DF',
        500: '#4750D5',
        600: '#2C35BF',
        700: '#222995',
        800: '#191E6C',
        900: '#0F1242',
      },
      accent: {
        50: '#FBF4FB',
        100: '#F5E0F3',
        200: '#EFCDEC',
        300: '#E5B3E1',
        400: '#D47DCC',
        500: '#C757BD',
        600: '#B03BA6',
        700: '#892E82',
        800: '#64215E',
        900: '#3D143A',
      },
      gray: {
        50: '#F5F5FA',
        100: '#E4E5F1',
        200: '#CFD0E2',
        300: '#B3B5CC',
        400: '#9496B8',
        500: '#6C6F93',
        600: '#47496B',
        700: '#32344B',
        800: '#1D1E30',
        900: '#0A0B12',
      },
      success: {
        50: '#F3FCF7',
        100: '#DEF7EA',
        200: '#C9F3DD',
        300: '#ACECCA',
        400: '#72DFA5',
        500: '#2BBB6E',
        600: '#219156',
        700: '#18683D',
        800: '#0E3E25',
        900: '#082114',
      },
      warning: {
        50: '#FDF8F2',
        100: '#FAECDB',
        200: '#F7E0C5',
        300: '#F2CFA6',
        400: '#E9AD67',
        500: '#DF8620',
        600: '#B26B1A',
        700: '#865013',
        800: '#59360D',
        900: '#472B0A',
      },
      danger: {
        50: '#FCF3F3',
        100: '#F7DEDF',
        200: '#F3C9CA',
        300: '#ECACAE',
        400: '#DF7275',
        500: '#D5474C',
        600: '#BF2C31',
        700: '#952226',
        800: '#6C191C',
        900: '#420F11',
      },
    },
    extend: {},
  },
  plugins: [],
}
```

In case we want to keep also de Tailwind colors, we can move the colors object inside the `extend: {}`
