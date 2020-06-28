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

