# Menus and Pickers
## Types of Menus

A menu is a set of options. The user can select from a menu to perform a function, for example searching for information, saving information, editing information, or navigating to a screen. The figure below shows the types of menus that the Android system offers. 

<br>


<p align="center">
<img  src="https://github.com/saisankar12/document/blob/master/saisankar_concept_images/types_menus.png">
</p>

1. **App bar with Options menu:** Appears in the app bar and provides the primary options that affect use of the app itself.
    - Examples of menu options: 
      - Search to perform a search
      - Share to share a link
      - Settings** to navigate to a Settings *Activity*.
2. **Contextual menu:** Appears as a floating list of choices when the user performs a long tap on an element on the screen. 
    - Examples of menu options: 
      - Edit to edit the element
      - Delete to delete it
      - Share to share it over social media.
3. **Contextual action bar:** Appears at the top of the screen overlaying the app bar, with action items that affect the selected element or elements. 
    - Examples of menu options: 
        - Edit, Share, and Delete for one or more selected elements.
4. **Popup menu:** Appears anchored to a View such as an ImageButton, and provides an overflow of actions or the second part of a two-part command. 
    - Example of a popup menu: 
      - the Gmail app anchors a popup menu to the app bar for the message view with Reply, Reply All, and Forward.

## App bar with options menu

The app bar (also called the action bar) is a dedicated space at the top of each Activity screen. When you create an _Activity_ from a template (such as Empty Template), an app bar is automatically included for the _Activity_.

The app bar by default shows the app title, or the name defined in AndroidManifest.xml by the android:label attribute for the Activity. The app bar may also include the Up button for navigating up to the parent activity. Up navigation is described in the chapter on using the app bar for navigation.

The options menu in the app bar usually provides navigation to other screens in the app, or options that affect using the app itself. (The options menu should not include options that act on an element on the screen. For that you use a contextual menu, described later in this chapter.)

For example, your options menu might let the user navigate to another activity to place an order. Or your options menu might let the user change settings or profile information, or do other actions that have a global impact on the app.

The options menu appears in the right corner of the app bar. The app bar is split into four functional areas that apply to most apps, as shown in the figure below.

<br>
<p align="center">
<img  src="https://github.com/saisankar12/document/blob/master/saisankar_concept_images/option%20_menu.png">
</p>
<br>

In the figure above:

1. Navigation button or Up button: Use a navigation button in this space to open a navigation drawer, or use an Up button for navigating up through your app's screen hierarchy to the parent activity. Both are described in the next chapter.
2. Title: The title in the app bar is the app title, or the name defined in **_AndroidManifest.xml_** by the **android:label** attribute for the activity.
3. Action icons for the options menu: Each action icon appears in the app bar and represents one of the options menu's most frequently used items. Less frequently used options menu items appear in the overflow options menu.
4. Overflow options menu: The overflow icon opens a popup with option menu items that are not shown as icons in the app bar.

