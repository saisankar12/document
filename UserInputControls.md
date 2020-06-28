## Input controls

This chapter introduces the Android _input controls_. Input controls are interactive elements in your app's UI that accept data input. Users input data to apps by entering text or numbers into fields using the on-screen keyboard. Users also select options from checkboxes, radio buttons, and drop-down menus, and they change settings and turn on or turn off certain features.

Android provides a variety of input controls for your UI. The figure below shows some popular ones.

<br>
<p align="center">
<img  src="https://github.com/saisankar12/document/blob/master/saisankar_concept_images/user_input_controls_composite.png">
</p>
<br>

In the figure above:

1. [EditText](https://developer.android.com/reference/android/widget/EditText.html) field (subclass of TextView) for entering text using a keyboard
2. [SeekBar](https://developer.android.com/reference/android/widget/SeekBar.html) for sliding left or right to a setting
3. [CheckBox](https://developer.android.com/reference/android/widget/CheckBox.html) elements for selecting one or more options
4. [RadioGroup](https://developer.android.com/reference/android/widget/RadioGroup.html) of [RadioButton](https://developer.android.com/reference/android/widget/RadioButton.html) elements for selecting one option
5. [Switch](https://developer.android.com/reference/android/widget/Switch.html) for turning on or turning off an option
6. [Spinner](https://developer.android.com/reference/android/widget/Spinner.html) drop-down menu for selecting one option

When your app needs to get data from the user, try to make the process as easy for the user as it can be. For example, anticipate the source of the data, minimize the number of user gestures such as taps and swipes, and pre-fill forms when possible.

The user expects input controls to work in your app the same way they work in other apps. For example, users expect a _Spinner_ to show a drop-down menu, and they expect text-editing fields to show a keyboard when tapped. Don't violate established expectations, or you'll make it harder for your users to use your app.

### Input controls for making choices

Android offers ready-made input controls for the user to select one or more choices:

* [CheckBox](https://developer.android.com/reference/android/widget/CheckBox.html): Select one or more choices from a set of choices by tapping or clicking checkboxes.
* [RadioGroup](https://developer.android.com/reference/android/widget/RadioGroup.html) of radio buttons: Select one choice from a set of choices by clicking one circular "radio" button. Radio buttons are useful if you are providing only two or three choices.
* [ToggleButton](https://developer.android.com/reference/android/widget/ToggleButton.html) and [Switch](https://developer.android.com/reference/android/widget/Switch.html): Turn an option on or off.
* [Spinner](https://developer.android.com/reference/android/widget/Spinner.html): Select one choice from a set of choices in a drop-down menu. A Spinner is useful for three or more choices, and takes up little room in your layout.

### Input controls and the View focus

If your app has several UI input elements, which element gets input from the user first? 
  * For example, if you have several _EditText_ elements for the user to enter text, which element (that is, which View) receives the text? The [View](https://developer.android.com/reference/android/view/View.html) that "has the focus" receives user input.

Focus indicates which _View_ is selected. The user can initiate focus by tapping on a _View_, for example a specific _EditText_ element. You can define a focus order that defines how focus moves from one element to another when the user taps the Return key, Tab key, or arrow keys. You can also control focus programmatically by calling _requestFocus()_ on any _View_ that is focusable.

In addition to being focusable, input controls can be _clickable_. If a view's clickable attribute is set to _true_, then the view can react to click events. You can also make an element clickable programmatically.

What's the difference between focusable and clickable?

  * A _focusable_ view is allowed to gain focus from a touchscreen, external keyboard, or other input device.
  * A _clickable_ view is any view that reacts to being tapped or clicked.
  
Android-powered devices use many input methods, including directional pads (D-pads), trackballs, touchscreens, external keyboards, and more. Some devices, like tablets and smartphones, are navigated primarily by touch. Other device have no touchscreen. Because a user might navigate through your UI with an input device such as D-pad or a trackball, make sure you do the following:

* Make it visually clear which View has focus, so that the user knows where the input goes.
* Explicitly set the focus in your code to provide a path for users to navigate through the input elements using directional keys or a trackball.

Fortunately, in most cases you don't need to control focus yourself. Android provides "touch mode" for devices that respond to touch, such as smartphones and tablets. When the user begins interacting with the UI by touching it, only View elements with _isFocusableInTouchMode()_ set to _true_, such as text input fields, are focusable. Other _View_ elements that are touchable, such as _Button_ elements, don't take focus when touched. If the user clicks a directional key or scrolls with a trackball, the device exits "touch mode" and finds a view to take focus.

Focus movement is based on a natural algorithm that finds the nearest neighbor in a given direction:

* When the user taps the screen, the topmost View under the tap is in focus, providing touch access for the child View elements of the topmost View.
* If you set an EditText view to a single line (such as the textPersonName value for the [android:inputType](https://developer.android.com/reference/android/widget/TextView.html#attr_android:inputType) attribute), the user can tap the right-arrow key on the on-screen keyboard to close the keyboard and shift focus to the next input control View based on what the Android system finds.

  The system usually finds the nearest input control in the same direction the user was navigating (up, down, left, or right).

  If there are multiple input controls that are nearby and in the same direction, the system scans from left to right, top to bottom.

* Focus can also shift to a different View if the user interacts with a directional control, such as a D-pad or trackball.

You can influence the way Android handles focus by arranging input controls such as _EditText_ elements in a certain layout from left to right and top to bottom, so that focus shifts from one to the other in the sequence you want.

If the algorithm does not give you what you want, you can override it by adding the _nextFocusDown, nextFocusLeft, nextFocusRight,_ and _nextFocusUp_ XML attributes to your layout file:

1. Add one of these attributes to a View to decide where to go upon leaving the View—in other words, which View should be the next View.
2. Define the value of the attribute to be the id of the next View. For example:

```xml
<LinearLayout
    <!-- Other attributes... --> 
    android:orientation="vertical" >

    <Button android:id="@+id/top"
          <!-- Other Button attributes... --> 
          android:nextFocusUp="@+id/bottom" />

    <Button android:id="@+id/bottom"
          <!-- Other Button attributes... -->
          android:nextFocusDown="@+id/top"/>

</LinearLayout>
```

In a vertical _LinearLayout_, navigating up from the first _Button_ would not ordinarily go anywhere, nor would navigating down from the second _Button_. But in the example above, the 
_top_ Button has specified the bottom Button as the nextFocusUp (and vice versa), so the navigation focus will cycle from top-to-bottom and bottom-to-top.

To declare a View as focusable in your UI (when it is traditionally not), add the _android:focusable_ XML attribute to the View in the layout, and set its value to true. You can also declare a View as focusable while in "touch mode" by setting android:focusableInTouchMode set to true.

You can also explicitly set the focus or find out which View has focus by using the following methods:

* Call [onFocusChanged](https://developer.android.com/reference/android/view/View.html#onFocusChanged(boolean,%20int,%20android.graphics.Rect)) to determine where focus came from.
* To find out which View currently has the focus, call [Activity.getCurrentFocus()](https://developer.android.com/reference/android/app/Activity.html#getCurrentFocus()), or use [ViewGroup.getFocusedChild()](https://developer.android.com/reference/android/view/ViewGroup.html#getFocusedChild()) to return the focused child of a _View_ (if any).
* To find the _View_ in the hierarchy that currently has focus, use [findFocus()](https://developer.android.com/reference/android/view/ViewGroup.html#findFocus()).
* Use [requestFocus](https://developer.android.com/reference/android/view/View.html#requestFocus()) to give focus to a specific View.
* To change whether a View can take focus, call [setFocusable](https://developer.android.com/reference/android/view/View.html#setFocusable(boolean)).
* To set a listener that is notified when the View gains or loses focus, use [setOnFocusChangeListener](https://developer.android.com/reference/android/view/View.html#setOnFocusChangeListener(android.view.View.OnFocusChangeListener)).

you learn more about focus with EditText elements.

### Checkboxes

Use a set of checkboxes when you want the user to select any number of choices, including zero choices:

* Each checkbox is independent of the other boxes in the set, so selecting one box doesn't clear the other boxes. (If you want to limit the user's selection to one choice, use radio buttons.)
* A user can clear a checkbox that was already selected.

Users expect checkboxes to appear in a vertical list, like a to-do list, or side-by-side if the labels are short.

<br>
<p align="center">
<img  src="https://github.com/saisankar12/document/blob/master/saisankar_concept_images/checkboxes.png">
</p>
<br>

Each checkbox is a separate [CheckBox](https://developer.android.com/reference/android/widget/CheckBox.html) element in your XML layout. To create multiple checkboxes in a vertical orientation, use a vertical LinearLayout:

```xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
        android:orientation="vertical"
        android:layout_width="fill_parent"
        android:layout_height="fill_parent">

        <CheckBox android:id="@+id/checkbox1_chocolate"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="ChocolateSyrup" />
        <CheckBox android:id="@+id/checkbox2_sprinkles"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Sprinkles" />
        <CheckBox android:id="@+id/checkbox3_nuts"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="CrushedNuts" />

</LinearLayout>
```

Typically programs retrieve the state of each _CheckBox_ when a user taps or clicks a **Submit** or **Done** _Button_ in the same _Activity_, which uses the _android:onClick_ attribute to call a method such as _onSubmit()_:

```xml
<Button
   android:layout_width="wrap_content"
   android:layout_height="wrap_content"
   android:text="@string/submit"
   android:onClick="onSubmit"/>
```

The callback method—_onSubmit()_ in the example above—must be _public_, return _void_, and define a _View_ as a parameter (the view that was clicked). In this callback method you can determine whether a _CheckBox_ is selected by using the [isChecked()](https://developer.android.com/reference/android/widget/CompoundButton.html#isChecked()) method (inherited from [CompoundButton](https://developer.android.com/reference/android/widget/CompoundButton.html)).

The _isChecked()_ method returns _true_ if there is a check mark in the box. For example, the following statement assigns _true_ or _false_ to _checked_, depending on whether the checkbox is checked:

```java
public void onSubmit(View view) {
        CheckBox ch_java = findViewById(R.id.java);
        CheckBox ch_android = findViewById(R.id.android);
        StringBuilder builder = new StringBuilder();
        if(ch_java.isChecked()){
            builder.append(ch_java.getText().toString()+",");
        }

        if(ch_android.isChecked()){
            builder.append(ch_android.getText().toString());
        }
// Code to display the result...
}
```

**Tip**: To respond quickly to a _CheckBox_—such as display a message (like an alert), or show a set of further options—you can use the _android:onClick_ attribute in the XML layout for each _CheckBox_ to declare the callback method for that _CheckBox_. The callback method must be defined within the _Activity_ that hosts this layout.

For more information about checkboxes, see [Checkboxes](https://developer.android.com/guide/topics/ui/controls/checkbox.html) in the Android developer documentation.

### Radio buttons

Use radio buttons when you have two or more options that are mutually exclusive. When the user selects one, the others are automatically deselected. (If you want to enable more than one selection from the set, use checkboxes.)

<br>
<p align="center">
<img  src="https://github.com/saisankar12/document/blob/master/saisankar_concept_images/radiobuttons.png">
</p>
<br>

