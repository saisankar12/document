## Material Design

Material Design is a visual design philosophy that Google created in 2014. The aim of Material Design is a unified user experience across platforms and device sizes. Material Design includes a set of guidelines for style, layout, motion, and other aspects of app design. The complete guidelines are available in the [Material Design spec](https://material.io/design/).

Material Design is for desktop web applications as well as for mobile apps. This chapter focuses only on Material Design for mobile apps on Android.

### Principles of Material Design

In Material Design, elements in your Android app behave like real world materials: they cast shadows, occupy space, and interact with each other.

### Bold, graphic, intentional

Material Design involves deliberate color choices, edge-to-edge imagery, large-scale typography, and intentional white space that create a bold and graphic interface.

Emphasize user actions in your app so that the user knows right away what to do, and how to do it. For example, highlight things that users can interact with, such as buttons, EditText fields, and switches.

<br>
<p align="center">
<img  src="https://github.com/saisankar12/document/blob/master/saisankar_concept_images/bold_fab.png">
</p>
<br>

In the above figure, #1 is a [FloatingActionButton](https://developer.android.com/reference/android/support/design/widget/FloatingActionButton.html) with a pink accent color.

### Meaningful motion

Make animations and other motions in your app meaningful, so they don't happen at random. Use motions to reinforce the idea that the user is the app's primary mover. For example, design your app so that most motions are initiated by the user's actions, not by events outside the user's control. You can also use motion to focus the user's attention, give the user subtle feedback, or highlight an element of your app.

When your app presents an object to the user, make sure the motion doesn't break the continuity of the user's experience. For example, the user shouldn't have to wait for an animation or transition to complete.

The Motion section in this chapter goes into more detail about how to use motion in your app.

### Colors

Material Design principles include the use of bold color.

### Material Design color palette

The [Material Design color palette](https://material.io/design/color/the-color-system.html) contains colors to choose from, each with a primary color and shades labeled from 50 to 900:

* Choose a color labeled "500" as the primary color for your brand. Use that color and shades of that color in your app.
* Choose a contrasting color as your accent color and use it to create highlights in your app. Select any color that starts with "A".

When you create an Android project in Android Studio, a sample Material Design color scheme is selected for you and applied to your theme. In _colors.xml_ in the _values_ folder, three _<color>_ elements are defined, **_colorPrimary, colorPrimaryDark,_** and **_colorAccent_**:

```xml
<resources>
    <color name="colorPrimary">#3F51B5</color>
    <!-- Indigo. -->
    <color name="colorPrimaryDark">#303F9F</color>
    <!-- A darker shade of indigo. -->
    <color name="colorAccent">#FF4081</color>
    <!-- A shade of pink. -->
</resources>
```

In _styles.xml_ in the _values_ folder, the three defined colors are applied to the default theme, which applies the colors to some app elements by default:

* **_colorPrimary_** is used by several _View_ elements by default. For example, in the _AppTheme_ theme, _colorPrimary_ is used as the background color for the action bar. Change this value to the "500" color that you select as your brand's primary color.
* **_colorPrimaryDark_** is used in areas that need to slightly contrast with your primary color, for example the status bar above the app bar. Set this value to a slightly darker version of your primary color.
* **_colorAccent_** is used as the highlight color for several _View_ elements. It's also used for switches in the "on" position, [FloatingActionButton](https://developer.android.com/reference/android/support/design/widget/FloatingActionButton.html), and more.

In the screenshot below, the background of the action bar uses colorPrimary (indigo), the status bar uses colorPrimaryDark (a darker shade of indigo), and the switch in the "on" position (#1 in the figure below) uses colorAccent (a shade of pink).

<br>
<p align="center">
<img  src="https://github.com/saisankar12/document/blob/master/saisankar_concept_images/bold_switch.png">
</p>
<br>

In summary, here's how to use the Material Design color palette in your Android app:

1. Pick a primary color for your app from [Material Design color palette](https://material.io/design/color/the-color-system.html) and copy its hex value into the _colorPrimary_ item in _colors.xml_.
2. Pick a darker shade of this color and copy its hex value into the _colorPrimaryDark_ item.
3. Pick an accent color from the shades starting with an "A" and copy its hex value into the _colorAccent_ item.
4. If you need more colors, create additional _<color>_ elements in the _colors.xml_ file. For example, you could pick a lighter version of indigo and create an additional _<color>_ element named _colorPrimaryLight_. (The name is up to you.)
  
```xml
 <color name="colorPrimaryLight">#9FA8DA</color>
 <!-- A lighter shade of indigo. -->
```

To use this color, reference it as _@color/colorPrimaryLight_.

Changing the values in _colors.xml_ automatically changes the colors of the _View_ elements in your app, because the colors are applied to the theme in _styles.xml_.

### Contrast

Make sure all the text in your app's UI contrasts with its background. Where you have a dark background, make the text on top of it a light color, and vice versa. This kind of contrast is important for readability and [accessibility](https://material.io/design/usability/accessibility.html#hierarchy), because not all people see colors the same way.

If you use a platform theme such as [Theme.AppCompat](https://developer.android.com/reference/android/support/v7/appcompat/R.style.html#Theme_AppCompat), contrast between text and its background is handled for you. For example:

* If your theme inherits from **_Theme.AppCompat_**, the system assumes you are using a dark background. Therefore all of the text is near white by default.
* If your theme inherits from **_Theme.AppCompat.Light_**, the text is near black, because the theme has a light background.
* If you use the **_Theme.AppCompat.Light.DarkActionBar_** theme, the text in the action bar is near white, to contrast with the action bar's dark background. The rest of the text in the app is near black, to contrast with the light background.

Use color contrast to create visual separation among the elements in your app. Use your _colorAccent_ color to call attention to key UI elements such as _FloatingActionButton_ and switches in the "on" position.

### Opacity

Your app can display text with different degrees of opacity to convey the relative importance of information. For example, text that's less important might be nearly transparent (low opacity).

Set the _android:textColor_ attribute using any of these formats: **_"#rgb", "#rrggbb", "#argb",_** or **_"#aarrggbb"_**. To set the opacity of text, use the **_"#argb"_** or **_"#aarrggbb"_** format and include a value for the alpha channel. The alpha channel is the _a_ or the aa at the start of the _textColor_ value.

The maximum opacity value, _FF_ in hex, makes the color completely opaque. The minimum value, _00_ in hex, makes the color complete transparent.

To determine what hex number to use in the alpha channel:

1. Decide what level of opacity you want to use, as a percentage. The level of opacity used for text depends on whether your background is dark or light. To find out what level of opacity to use in different situations, see the [Text color portion](https://material.io/design/color/text-legibility.html#text-backgrounds) of the Material Design guide.
2. Multiply that percentage, as a decimal value, by 255. For example, if you need primary text that's 87% opaque, multiply 0.87 x 255. The result is 221.85.
3. Round the result to the nearest whole number: 222.
4. Use a hex converter to convert the result to hex: DE. If the result is a single value, prefix it with 0.

In the following XML code, the background of the text is dark, and the color of the primary text is 87% white _(deffffff)_. The first two numbers of the color code (de) indicate the opacity.

```xml
<TextView
   android:layout_width="match_parent"
   android:layout_height="wrap_content"
   android:text="Hello World!"
   android:textSize="45dp"
   android:background="@color/colorPrimaryDark"
   android:textColor="#deffffff"/>
```

Instead of using gray text and icons on top of colored backgrounds, create better contrast by displaying white or black text with reduced opacity.

For example, black text displayed at 75% opacity on a green background gives the text an appearance of black, with a hint of green.

Alternatively, you can calculate the color of text by doing the following:

* Place the color black at reduced opacity in front of a green background
* Identify the hex value of the resulting darkened green color
* Use that hex value of that color for your text

In this case, if the surface behind the text changes color, you must update the hex color as well.

<br>
<p align="center">
<img  src="https://github.com/saisankar12/document/blob/master/saisankar_concept_images/opacity_do.PNG">
</p>
<br>
Use a transparent version of black on a colored surface to preserve legibility.
<br>
<p align="center">
<img  src="https://github.com/saisankar12/document/blob/master/saisankar_concept_images/opacity_don't%20do.PNG">
</p>
<br>
Avoid using opaque gray text that isn’t legible on colored surfaces.



