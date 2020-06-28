## Navigation drawer

A navigation drawer is a panel that usually displays navigation options on the left edge of the screen, as shown on the right side of the figure below. It is hidden most of the time, but is revealed when the user swipes a finger from the left edge of the screen or touches the navigation icon in the app bar, as shown on the left side of the figure below.

<br>
<p align="center">
<img  src="https://github.com/saisankar12/document/blob/master/saisankar_concept_images/dg_nav_drawer_composite.png">
</p>
<br>

In the figure above:

1. Navigation icon in the app bar
2. Navigation drawer
3. Navigation drawer menu item

A good example of a navigation drawer is in the Gmail app, which provides access to the inbox, labeled email folders, and settings. The best practice for employing a navigation drawer is to provide descendant navigation from the parent _Activity_ to all of the other child screens in an app. It can display many navigation targets at once—for example, it can contain buttons (like a dashboard), tabs, or a list of items (like the Gmail drawer).

To make a navigation drawer in your app, you need to create the following layouts:

* A navigation drawer as the Activity layout root ViewGroup
* A navigation View for the drawer itself
* An app bar layout that includes room for a navigation icon button
* A content layout for the Activity that displays the navigation drawer
* A layout for the navigation drawer header

Follow these general steps:

1. Populate the navigation drawer menu with item titles and icons.
2. Set up the navigation drawer and item listeners in the Activity code.
3. Handle the navigation menu item selections.

Adding Dependency:

```gradle
implementation 'com.google.android.material:material:1.1.0'
```

### Creating the navigation drawer layout

To create a navigation drawer layout, use the [DrawerLayout](https://developer.android.com/reference/android/support/v4/widget/DrawerLayout.html) APIs available in the [Support Library](https://developer.android.com/topic/libraries/support-library/). For design specifications, follow the design principles for navigation drawers in the [Navigation Drawer](https://material.io/design) design guide.

To add a navigation drawer, use a DrawerLayout as the root ViewGroup of your Activity layout. Inside the DrawerLayout, add one View that contains the main content for the screen (your primary layout when the drawer is hidden) and another View, typically a [NavigationView](https://developer.android.com/reference/android/support/design/widget/NavigationView.html), that contains the contents of the navigation drawer.

**Tip**: To make your layouts simpler to understand, use the include tag to include an XML layout within another XML layout.

For example, the following layout uses:

* A DrawerLayout as the root of the Activity layout in activity_main.xml.
* The main content of screen defined in the app_bar_main.xml layout file.
* A NavigationView that represents a standard navigation menu that can be populated by a menu resource XML file.

Refer to the figure below that corresponds to this layout:

### activity_main.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.drawerlayout.widget.DrawerLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/drawerlayout"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <include
        layout="@layout/content_main"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />

    <com.google.android.material.navigation.NavigationView
        android:id="@+id/navigation_view"
        android:layout_width="wrap_content"
        android:layout_height="match_parent"
        android:layout_gravity="start"
        android:fitsSystemWindows="true"
        app:headerLayout="@layout/nav_header"
        app:itemIconTint="#3F51B5"
        app:menu="@menu/menu" />

</androidx.drawerlayout.widget.DrawerLayout>
```
