# Menus
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
   <br>  
       
* Use the **_app:showAsAction_** attribute to show menu items as icons in the app bar, with the following values:

     - **_"always":_** Always place this item in the app bar. Use this only if it's critical that the item appear in the app bar (such as a Search icon). If you set   multiple items to always appear in the app bar, they might overlap something else in the app bar, such as the app title.
     - **_"ifRoom":_** Only place this item in the app bar if there is room for it. If there is not enough room for all the items marked **_"ifRoom"_**, the items with the lowest **_orderInCategory_** values are displayed in the app bar. The remaining items are displayed in the overflow menu.
     - **_"never":_** Never place this item in the app bar. Instead, list the item in the app bar's overflow menu.
     - **_"withText":_** Also include the title text (defined by **_android:title_**) with the item. This attribute is used primarily to include the title with the icon in the app bar, because if the item appears in the overflow menu, the title text appears regardless.
       
### Position attributes
       
* Use the **_android:orderInCategory_** attribute to specify the order in which the menu items appear in the menu, with the lowest number appearing higher in the menu. This is usually the order of importance of the item within the menu. For example, if you want **Order** to be first, followed by **Status, Favorites,** and **Contact**, the following table shows the priority of these items in the menu:
       <br>
           
    Menu item | orderInCategory attribute
    ----------|----------------------------
    Order | 10 
    Status | 20
    Favorites | 30 
    Contact | 40 
       
<br>
        <p align="center">
            <img  src="https://github.com/saisankar12/document/blob/master/saisankar_concept_images/orderattribute.PNG">
        </p>
 <br>
     
```xml 
     <item
        android:title="Call"
        android:id="@+id/call"
        android:icon="@mipmap/call"
        android:orderInCategory="40"
        app:showAsAction="always"
        />
  ```
   3. onCreateOptionsMenu() to inflate the menu
        - If you start an app project using the Basic Activity template, the template adds the code for inflating the options menu with **_MenuInflater
_**, so you can skip this step.

        - If you are not using the Basic Activity template, inflate the menu resource in your activity by overriding the [onCreateOptionsMenu()](https://developer.android.com/reference/android/app/Activity.html#onCreateOptionsMenu(android.view.Menu)) method and using the [getMenuInflater()](https://developer.android.com/reference/android/app/Activity.html#getMenuInflater()) method of the **Activity** class.

        - The **getMenuInflater()** method returns a [MenuInflater](https://developer.android.com/reference/android/view/MenuInflater.html), which is a class used to instantiate menu XML files into **Menu** objects. The **MenuInflater** class provides the [inflate()](https://developer.android.com/reference/android/view/MenuInflater.html#inflate(int,%20android.view.Menu)) method, which takes two parameters:
            - The resource **_id_** for an XML layout resource to load (**_R.menu.menu_main_** in the following example).
            - The [Menu](https://developer.android.com/reference/android/view/Menu.html) to inflate into (_menu_ in the following example)
```java
     @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        getMenuInflater().inflate(R.menu.menu,menu);
        return super.onCreateOptionsMenu(menu);
    }
```
     
   4. onClick attribute or onOptionsItemSelected() 
        - However, the [onOptionsItemSelected()](https://developer.android.com/reference/android/app/Activity.html#onOptionsItemSelected(android.view.MenuItem)) method can handle all the menu-item clicks in one place and determine which menu item the user clicked. This makes your code easier to understand.
```java
     @Override
    public boolean onOptionsItemSelected(@NonNull MenuItem item) {
        //Action
        return super.onOptionsItemSelected(item);
    }
```
<br>

* For example, you can use a **_switch case_** block to call the appropriate method (such as **Toast** message) based on the menu item's **_id_.** You retrieve the **_id_** using the [getItemId()](https://developer.android.com/reference/android/widget/Adapter.html#getItemId(int)) method:
<br>

```java
     @Override
    public boolean onOptionsItemSelected(@NonNull MenuItem item) {
        switch (item.getItemId()){
            case R.id.notification:
                Toast.makeText(this, ""+item.getTitle(), Toast.LENGTH_SHORT).show();
                break;
            case R.id.dial:
                Toast.makeText(this, ""+item.getTitle(), Toast.LENGTH_SHORT).show();
                break;
            case R.id.call:
                Toast.makeText(this, ""+item.getTitle(), Toast.LENGTH_SHORT).show();
                break;
        }
        return super.onOptionsItemSelected(item);
    }
```
<br>
    
## Codeing Implementation
- Create Start new android Studio Project and Select Empty Activity
- No need modify your **_activity_main.xml_**, If any requriments you can modify it.
- Create Android Resourse Directory with the name of menu 
- Create menu resourse xml file
- adding items
- intialization in java file 
- handling the click events
    
### activity_main.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />
    
</androidx.constraintlayout.widget.ConstraintLayout>


```
 ### menu.xml
 ```xml
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto">

    <item
        android:id="@+id/notification"
        android:title="Search" />
    <item
        android:id="@+id/dial"
        android:title="Dail" />
    <item
        android:id="@+id/call"
        android:icon="@mipmap/call"
        android:title="Call"
        app:showAsAction="always" />
    <item
        android:id="@+id/user"
        android:title="User" />
    
</menu>
    
 ```
    
### MainActivity.java
```java
package com.example.menuspickers;


import android.os.Bundle;
import android.view.Menu;
import android.view.MenuItem;
import android.widget.Toast;
import androidx.annotation.NonNull;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        getMenuInflater().inflate(R.menu.menu, menu);
        return super.onCreateOptionsMenu(menu);
    }

    @Override
    public boolean onOptionsItemSelected(@NonNull MenuItem item) {

        switch (item.getItemId()) {
            case R.id.notification:
                // we are getting menu item title here
                Toast.makeText(this, ""+item.getTitle(), Toast.LENGTH_SHORT).show();
                break;
            case R.id.dial:
                Toast.makeText(this, ""+item.getTitle(), Toast.LENGTH_SHORT).show();
                break;
            case R.id.call:
                Toast.makeText(this, ""+item.getTitle(), Toast.LENGTH_SHORT).show();
                break;
        }
        return super.onOptionsItemSelected(item);
    }

}
```
    
### Contextual menus
    
Use a contextual menu to allow users to take an action on a selected [View](https://developer.android.com/reference/android/view/View.html). Contextual menus are most often used for items in a [ListView](https://developer.android.com/reference/android/widget/ListView.html), [RecyclerView](https://developer.android.com/reference/android/support/v7/widget/RecyclerView.html), [GridView](https://developer.android.com/reference/android/widget/GridView.html), or other view collection in which the user can perform direct actions on each item.

* Android provides two kinds of contextual menus:

    * A **_context menu_**, shown on the left side in the figure below, appears as a floating list of menu items when the user performs a long tap on a _View_. It is typically used to modify the View or use it in some fashion. 
        - For example, a context menu might include 
            - **Edit** to edit the contents of a _View_, 
            - **Delete** to delete a _View_,
            - **Share** to share a _View_ over social media. Users can perform a contextual action on one selected View at a time.

    * A **_contextual action bar_**, shown on the right side of the figure below, appears at the top of the screen in place of the app bar or underneath the app bar, with action items that affect one or more selected _View_ elements. Users can perform an action on multiple _View_ elements at once, if your app allows it.
    
<br>
        <p align="center">
            <img  src="https://github.com/saisankar12/document/blob/master/saisankar_concept_images/Context%20Menu%20Types.jpg">
        </p>
 <br>

### Floating context menu

<p>
    The familiar resource-inflate design pattern is used to create a context menu, modified to include registering (associating) the context menu with a _View_. The pattern consists of the steps shown in the figure below.
<p>

<br>
        <p align="center">
            <img  src="https://github.com/saisankar12/document/blob/master/saisankar_concept_images/contextmenufloating.png">
        </p>
 <br>

#### Steps to Implement Context Menu:
     
1. Create an XML menu resource file for the menu items. Assign appearance and position attributes as described in the previous section for the options menu.
2. Register a View to the context menu using the [registerForContextMenu()](https://developer.android.com/reference/android/app/Activity.html#registerForContextMenu(android.view.View)) method of the _Activity_ class.
3. Implement the [onCreateContextMenu()](https://developer.android.com/reference/android/view/View.OnCreateContextMenuListener.html#onCreateContextMenu(android.view.ContextMenu,%20android.view.View,%20android.view.ContextMenu.ContextMenuInfo)) method in your _Activity_ to inflate the menu.
4. Implement the [onContextItemSelected()](https://developer.android.com/reference/android/app/Activity.html#onContextItemSelected(android.view.MenuItem)) method in your _Activity_ to handle menu-item clicks.
5. Create a method to perform an action for each context menu item.
     
     
#### Creating the XML resource file
     
To create the XML menu resource directory and file, follow the steps in the previous section for the options menu. However, use a different name for the file, such as menu_context. Add the context menu items within _<item ... />_ tags.
     
For example, the following code defines the **_Edit_** menu item:
     
```xml
<item
   android:id="@+id/context_edit"
   android:title="Edit"
   android:orderInCategory="10"/>
```
    
### Registering a View to the context menu
     
To register a View to the context menu, call the [registerForContextMenu()](https://developer.android.com/reference/android/app/Activity.html#registerForContextMenu(android.view.View)) method with the View. Registering a context menu for a view sets the [View.OnCreateContextMenuListener](https://developer.android.com/reference/android/view/View.OnCreateContextMenuListener.html) on the View to this activity, so that [onCreateContextMenu()](https://developer.android.com/reference/android/app/Activity.html#onCreateContextMenu(android.view.ContextMenu,%20android.view.View,%20android.view.ContextMenu.ContextMenuInfo)) is called when it's time to show the context menu. (You implement onCreateContextMenu in the next section.)
     
For example, in the _onCreate()_ method for the _Activity_, you would add _registerForContextMenu()_:
     
```java
// Registering the context menu to the TextView of the article.
ListView names_list = findViewById(R.id.list);

// Create String Array
String[] s ={"Anusha","Pavan","Krishna","Siva","Masthan","Muni","Sai","Gopal","Chaitanya","Vara Prasad",
                "Anusha","Pavan","Krishna","Siva","Masthan","Muni","Sai","Gopal","Chaitanya","Vara Prasad"};

// For Displaying String Array Data in ListView, For That we need Create ArrayAdapter Like Below
ArrayAdapter<String> adapter=new ArrayAdapter<>(this,android.R.layout.simple_list_item_1,s);
     
// set Adapter to ListView, Then Only we can display the data in ListView        
lv.setAdapter(adapter);
registerForContextMenu(names_list);
```
     
Multiple views can be registered to the same context menu. If you want each item in a [TextView](https://developer.android.com/reference/android/widget/TextView.html) or [ListView](https://developer.android.com/reference/android/widget/ListView.html) or [GridView](https://developer.android.com/reference/android/widget/GridView.html) to provide the same context menu, register all items for a context menu by passing the [TextView](https://developer.android.com/reference/android/widget/TextView.html) or [ListView](https://developer.android.com/reference/android/widget/ListView.html) or [GridView](https://developer.android.com/reference/android/widget/GridView.html) to [registerForContextMenu()](https://developer.android.com/reference/android/app/Activity.html#registerForContextMenu(android.view.View)).
     
### Implementing the _onCreateContextMenu()_ method
     
When the registered View receives a long-click event, the system calls the [onCreateContextMenu()](https://developer.android.com/reference/android/view/View.OnCreateContextMenuListener.html#onCreateContextMenu(android.view.ContextMenu,%20android.view.View,%20android.view.ContextMenu.ContextMenuInfo)) method, which you can override in your _Activity_. (Long-click events are also called touch & hold events and _long-press_ events.)
     
The _onCreateContextMenu()_ method is where you define the menu items, usually by inflating a menu resource.

For example:

```java
     @Override
    public void onCreateContextMenu(ContextMenu menu, View v, ContextMenu.ContextMenuInfo menuInfo) {
        MenuInflater inflater = getMenuInflater();
        inflater.inflate(R.menu.menu,menu);
        super.onCreateContextMenu(menu, v, menuInfo);
    }
```
     
In the code above:

   - The _menu_ parameter for _onCreateContextMenu()_ is the context menu to be built.
   - The _v_ parameter is the _View_ registered for the context menu.
   - The _menuInfo_ parameter is extra information about the _View_ registered for the context menu. This information varies depending on the class of the _v_ parameter, which could be a _RecyclerView_ or a _GridView_.

   If you are registering a _RecyclerView_ or a _GridView_, you instantiate a [ContextMenu.ContextMenuInfo](https://developer.android.com/reference/android/view/ContextMenu.ContextMenuInfo.html) object to provide information about the item selected, and pass it as menuInfo, such as the row id, position, or child _View_.
     
The [MenuInflater](https://developer.android.com/reference/android/view/MenuInflater.html) class provides the [inflate()](https://developer.android.com/reference/android/view/MenuInflater.html#inflate(int,%20android.view.Menu)) method, which takes two parameters:

   - The resource _id_ for an XML layout resource to load. In the example above, the _id_ is _menu_context_.
   - The [Menu](https://developer.android.com/reference/android/view/Menu.html) to inflate into. In the example above, the _Menu_ is _menu_.

### Implementing the onContextItemSelected() method
     
When the user clicks on a menu item, the system calls the [onContextItemSelected()](https://developer.android.com/reference/android/app/Activity.html#onContextItemSelected(android.view.MenuItem)) method. You override this method in your _Activity_ in order to determine which menu item was clicked, and for which view the menu is appearing. You also use it to implement the appropriate action for the menu items, such as _editNote()_ , _shareNote()_ and _deleteNote()_ in the following code snippet for the **_Edit_** , **_Share_** and **_Delete_** menu items:
    
```java
     @Override
    public boolean onContextItemSelected(@NonNull MenuItem item) {
        switch (item.getItemId()){
            case R.id.share:
                // You can Write your requirement code here
                Toast.makeText(this, item.getTitle(), Toast.LENGTH_SHORT).show();
                break;
            case R.id.edit:
                // You can Write your requirement code here
                Toast.makeText(this, item.getTitle(), Toast.LENGTH_SHORT).show();
                break;
            case R.id.delete:
                // You can Write your requirement code here
                Toast.makeText(this, item.getTitle(), Toast.LENGTH_SHORT).show();
                break;
        }
        return super.onContextItemSelected(item);
    }
```
   
The above code snippet uses the [getItemId()](https://developer.android.com/reference/android/view/MenuItem.html#getItemId()) method to get the _id_ for the selected menu item, and uses it in a _switch case_ block to determine which action to take. The _id_ is the _android:id_ attribute assigned to the menu item in the XML menu resource file.

When the user performs a long-click on the article in the _ListView_, the floating context menu appears and the user can click a menu item.
     
<br>
        <p align="center">
            <img  src="https://github.com/saisankar12/document/blob/master/saisankar_concept_images/ContextMenuExample.jpg">
        </p>
 <br>
     
If you are using the _menuInfo_ information for a _RecyclerView_ or a _GridView_, you would add a statement before the _switch case_ block to gather the specific information about the selected _View_ (for _info_) by using [AdapterView.AdapterContextMenuInfo](https://developer.android.com/reference/android/widget/AdapterView.AdapterContextMenuInfo.html):
     
```java
     AdapterView.AdapterContextMenuInfo info = (AdapterView.AdapterContextMenuInfo) item.getMenuInfo();
```
     
### Contextual action bar Menu
     
A **_contextual action bar_** appears at the top of the screen to present actions the user can perform on a _View_ after long-clicking the _View_, as shown in the figure below.
     
     
<br>
        <p align="center">
            <img  src="https://github.com/saisankar12/document/blob/master/saisankar_concept_images/context_actionbar_singlecomponent.jpg">
        </p>
 <br>
     
In the above figure:

1. **Contextual action bar**. The bar offers three actions on the right side (**Edit**, **Share**, and **Delete**) and the Done button (left arrow icon) on the left side.
2. **View**. View on which a long-click triggers the contextual action bar.
     
The contextual action bar appears only when contextual action mode, a system implementation of [ActionMode](https://developer.android.com/reference/android/view/ActionMode.html), occurs as a result of the user performing a long-click on one or more selected _View_ elements.

_ActionMode_ represents UI mode for providing alternative interaction, replacing parts of the normal UI until finished. 
    - For example, text selection is implemented as an _ActionMode_, as are contextual actions that work on a selected item on the screen. Selecting a section of text or long-clicking a view triggers _ActionMode_.

While this mode is enabled, the user can select multiple items, if your app allows it. The user can also deselect items, and continue to navigate within the activity. _ActionMode_ is disabled when one of the following things occur:

* The user deselects all items.
* The user presses the Back button.
* The user taps **Done** (the left-arrow icon) on the left side of the action bar.
     
When _ActionMode_ is disabled, the contextual action bar disappears.

Follow these steps to create a contextual action bar, as shown in the figure below:
     
<br>
        <p align="center">
            <img  src="https://github.com/saisankar12/document/blob/master/saisankar_concept_images/dg_context_actionbar_design_pattern.png">
        </p>
 <br>
     
### Steps To Create ContextActionBar Menus:
     
1. Create an XML menu resource file for the menu items, and assign an icon to each one (as described in a previous section).
2. Set the long-click listener using [setOnLongClickListener()](https://developer.android.com/reference/android/view/View.html#setOnLongClickListener(android.view.View.OnLongClickListener)) to the View that should trigger the contextual action bar. Call [startActionMode()](https://developer.android.com/reference/android/app/Activity.html#startActionMode(android.view.ActionMode.Callback)) within the _setOnLongClickListener()_ method when the user performs a long tap on the View.
3. Implement the [ActionMode.Callback](https://developer.android.com/reference/android/view/ActionMode.Callback.html) interface to handle the _ActionMode_ lifecycle. Include in this interface the action for responding to a menu-item click in the [onActionItemClicked()](https://developer.android.com/reference/android/view/ActionMode.Callback.html#onActionItemClicked(android.view.ActionMode,%20android.view.MenuItem)) callback method.
4. Create a method to perform an action for each context menu item.
     
### Creating the XML resource file 
     
