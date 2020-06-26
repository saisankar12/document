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

The app bar (also called the action bar) is a dedicated space at the top of each **_Activity_** screen. When you create an **_Activity_** from a template (such as Empty Template), an app bar is automatically included for the **_Activity_**.

The app bar by default shows the app title, or the name defined in **_AndroidManifest.xml_** by the **_android:label_** attribute for the **_Activity_**. The app bar may also include the Up button for navigating up to the parent activity. Up navigation is described in the chapter on using the app bar for navigation.

The options menu in the app bar usually provides navigation to other screens in the app, or options that affect using the app itself. (The options menu should not include options that act on an element on the screen. For that you use a contextual menu, described later in this chapter.)

For example, your options menu might let the user navigate to another activity to place an order. Or your options menu might let the user change settings or profile information, or do other actions that have a global impact on the app.

The options menu appears in the right corner of the app bar. The app bar is split into four functional areas that apply to most apps, as shown in the figure below.

<br>
<p align="center">
<img  src="https://github.com/saisankar12/document/blob/master/saisankar_concept_images/option%20_menu.png">
</p>
<br>

In the figure above:

1. **_Navigation button or Up button:_** Use a navigation button in this space to open a navigation drawer, or use an Up button for navigating up through your app's screen hierarchy to the parent activity. Both are described in the next chapter.
2. **_Title:_** The title in the app bar is the app title, or the name defined in **_AndroidManifest.xml_** by the **android:label** attribute for the activity.
3. **_Action icons for the options menu:_** Each action icon appears in the app bar and represents one of the options menu's most frequently used items. Less frequently used options menu items appear in the overflow options menu.
4. **_Overflow options menu:_** The overflow icon opens a popup with option menu items that are not shown as icons in the app bar.


## Adding the options menu

Android provides a standard XML format to define options menu items. Instead of building the menu in your **_Activity_** code, you can define the menu and all its items in an XML [menu resource](https://developer.android.com/guide/topics/resources/menu-resource.html). A menu resource defines an application menu (options menu, context menu, or popup menu) that can be inflated with [MenuInflater](https://developer.android.com/reference/android/view/MenuInflater.html), which loads the resource as a [Menu](https://developer.android.com/reference/android/view/Menu.html) object in your Activity.

If you start an app project using the Basic Activity template, the template adds the menu resource for you and inflates the options menu with **_MenuInflater_**, so you can skip this step and go right to "Defining how menu items appear".

If you are not using the Basic Activity template, use the resource-inflate design pattern, which makes it easy to create an options menu. Follow these steps (refer to the figure below):

<br>
<p align="center">
<img  src="https://github.com/saisankar12/document/blob/master/saisankar_concept_images/dg_options_menu_design_pattern.png">
</p>
<br>

   1. **XML menu resource.** Create an XML menu resource file for the menu items, and assign appearance and position attributes as described in the next section.
   2. **Inflating the menu.** Override the [onCreateOptionsMenu()](https://developer.android.com/reference/android/app/Activity.html#onCreateOptionsMenu(android.view.Menu)) method in your **_Activity_** to inflate the menu.
   3. **Handling menu-item clicks.** Menu items are View elements, so you can use the **_android:onClick_** attribute for each menu item. However, the [onOptionsItemSelected()](https://developer.android.com/reference/android/app/Activity.html#onOptionsItemSelected(android.view.MenuItem)) method can handle all the menu-item clicks in one place and determine which menu item the user clicked, which makes your code easier to understand.
   4. **Performing actions.** Create a method to perform an action for each options menu item.


## Steps To Create App bar with options menu

   1. Create AndroidResourse directory
        * Select the **res** folder in the **Project > Android** pane and choose **File > New > Android resource directory.**
        <br>
        <p align="center">
            <img  src="https://github.com/saisankar12/document/blob/master/saisankar_concept_images/dircectory_creation.PNG">
        </p>
        <br>
        
        * Choose **menu** in the **Resource** type drop-down menu, and click **OK.**
        <br>
        <p align="center">
            <img  src="https://github.com/saisankar12/document/blob/master/saisankar_concept_images/menu_resourse_directory.PNG">
        </p>
        <br>
        
   2. XML menu resource (filename.xml)
       * Select the new **menu** folder, and choose **File > New > Menu resource file.**
        <br>
        <p align="center">
            <img  src="https://github.com/saisankar12/document/blob/master/saisankar_concept_images/menuxml_file_creation.PNG">
        </p>
        <br>
        
        * Enter the name, such as **Ex: menu_main**, and click **OK**. The new **_menu_main.xml_** file now resides within the **menu** folder.
        <br>
        <p align="center">
            <img  src="https://github.com/saisankar12/document/blob/master/saisankar_concept_images/menu_xml_file.PNG">
        </p>
        <br>
        
        * Add menu items using the **_<item ... />_** tag. <br>
        
               ```xml
<item
    android:id="@+id/user"
    android:title="User"/>
```
<br>

* Adding icons for menu items
       
        <br>
        <p align="center">
            <img  src="https://github.com/saisankar12/document/blob/master/saisankar_concept_images/image_creation.PNG">
        </p>
        <br>
        
* Icon and appearance attributes            
            - Use the following attributes to govern the menu item's appearance:
                  _android:icon:_ An image to use as the menu item icon. For example, the following menu item defines ic_order_white as its icon:
                  
```xml
<item
    android:id="@+id/user"
    android:title="User"
    android:icon="@mipmap/user"
        />
```
        
   3. onCreateOptionsMenu() to inflate the menu
   4. onClick attribute or onOptionsItemSelected() 
   5. Method to handle item click

