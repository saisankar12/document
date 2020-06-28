## Dialogs and pickers

A dialog is a window that appears on top of the display or fills the display, interrupting the flow of _Activity_. Dialogs inform users about a specific task and may contain critical information, require decisions, or involve multiple tasks.

For example, an alert dialog might require the user to click **Continue** after reading it, or give the user a choice to agree with an action by clicking a positive button (such as **OK** or **Accept**), or to disagree by clicking a negative button (such as **Cancel**).

You can also use a dialog to provide choices in the style of radio buttons, as shown on the right side of the figure below.

<br>
<p align="center">
<img  src="https://github.com/saisankar12/document/blob/master/saisankar_concept_images/dg_alerts_simple_dialog_composite.png">
</p>
<br>


The base class for all dialog components is a [Dialog](https://developer.android.com/reference/android/app/Dialog.html). There are several useful _Dialog_ subclasses for alerting the user on a condition, showing status or progress, displaying information on a secondary device, or selecting or confirming a choice, as shown on the left side of the figure below. The Android SDK also provides ready-to-use dialog subclasses such as pickers for picking a time or a date, as shown on the right side of the figure below. Pickers allow users to enter information in a predetermined, consistent format that reduces the chance for input error.

<br>
<p align="center">
<img  src="https://github.com/saisankar12/document/blob/master/saisankar_concept_images/dg_confirmation_and_picker_dialogs_composite.png">
</p>
<br>

Dialogs always retain focus until dismissed or a required action has been taken.

**Tip**: Best practices recommend using dialogs sparingly as they interrupt the user's workflow. Read the [Dialogs design guide](https://material.io/components/dialogs#usage) for additional best design practices, and [Dialogs](https://developer.android.com/guide/topics/ui/dialogs.html) in the Android developer documentation for code examples.

The [Dialog](https://developer.android.com/reference/android/app/Dialog.html) class is the base class for dialogs, but you should avoid instantiating _Dialog_ directly unless you are creating a custom dialog. For standard Android dialogs, use one of the following subclasses:

* **[AlertDialog](https://developer.android.com/reference/android/app/AlertDialog.html)**: A dialog that can show a title, up to three buttons, a list of selectable items, or a custom layout.
* **[DatePickerDialog](https://developer.android.com/reference/android/app/DatePickerDialog.html)**: A dialog with a predefined UI that lets the user select a date.
* **[TimePickerDialog](https://developer.android.com/reference/android/app/TimePickerDialog.html)**: A dialog with a predefined UI that lets the user select a time.

### Showing an alert dialog

Alerts are urgent interruptions, requiring acknowledgement or action, that inform the user about a situation as it occurs, or an action before it occurs (as in discarding a draft). You can provide buttons in an alert to make a decision. 

For example, an alert dialog might require the user to click **Continue** after reading it, or give the user a choice to agree with an action by clicking a positive button (such as **OK** or **Accept**), or to disagree by clicking a negative button (such as **Disagree** or **Cancel**).

Use the [AlertDialog](https://developer.android.com/reference/android/app/AlertDialog.html) subclass of the [Dialog](https://developer.android.com/reference/android/app/Dialog.html) class to show a standard dialog for an alert. The _AlertDialog_ class allows you to build a variety of dialog designs. An alert dialog can have the following regions (refer to the diagram below):


<br>
<p align="center">
<img  src="https://github.com/saisankar12/document/blob/master/saisankar_concept_images/alertdialog_output.jpg">
</p>
<br>

1. **_Title_**: A title is optional. Most alerts don't need titles. If you can summarize a decision in a sentence or two by either asking a question (such as, "Discard draft?") or making a statement related to the action buttons (such as, "Click OK to continue"), don't bother with a title. Use a title if the situation is high-risk, such as the potential loss of connectivity or data, and the content area is occupied by a detailed message, a list, or custom layout.
2. **_Content area_**: The content area can display a message, a list, or other custom layout.
3. **_Action buttons_**: You should use no more than three action buttons in a dialog, and most have only two.

### Building the AlertDialog

The [AlertDialog.Builder](https://developer.android.com/reference/android/app/AlertDialog.Builder.html) class uses the builder design pattern, which makes it easy to create an object from a class that has a lot of required and optional attributes and would therefore require a lot of parameters to build. Without this pattern, you would have to create constructors for combinations of required and optional attributes; with this pattern, the code is easier to read and maintain. For more information about the builder design pattern, see [Builder pattern](https://en.wikipedia.org/wiki/Builder_pattern).

Use [AlertDialog.Builder](https://developer.android.com/reference/android/app/AlertDialog.Builder.html) to build a standard alert dialog, with [setTitle()](https://developer.android.com/reference/android/app/AlertDialog.Builder.html#setTitle(int)) to set its title, [setMessage()](https://developer.android.com/reference/android/app/AlertDialog.Builder.html#setMessage(int)) to set its message, and [setPositiveButton()](https://developer.android.com/reference/android/app/AlertDialog.Builder.html#setPositiveButton(int,%20android.content.DialogInterface.OnClickListener)) and [setNegativeButton()](https://developer.android.com/reference/android/app/AlertDialog.Builder.html#setNegativeButton(int,%20android.content.DialogInterface.OnClickListener)) to set its buttons.

If _AlertDialog.Builder_ is not recognized as you enter it, you may need to add the following _import_ statements to the _Activity_:

```java
import android.content.DialogInterface;
import android.support.v7.app.AlertDialog;
```

The following creates the dialog object _(alertDialog)_ and sets the title (the string resource _alert_title_) and message (the string resource _alert_message_):

```java
AlertDialog.Builder alertDialog = new AlertDialog.Builder(this);
alertDialog.setTitle("This is Alert Dialog");
alertDialog.setMessage("Are you want close the App?");
```

### Setting the button actions for the alert dialog

Use the [setPositiveButton()](https://developer.android.com/reference/android/app/AlertDialog.Builder.html#setPositiveButton(int,%20android.content.DialogInterface.OnClickListener)) and [setNegativeButton()](https://developer.android.com/reference/android/app/AlertDialog.Builder.html#setNegativeButton(int,%20android.content.DialogInterface.OnClickListener)) methods to set the button actions for the alert dialog. These methods require a title for the button and the [DialogInterface.OnClickListener](https://developer.android.com/reference/android/content/DialogInterface.OnClickListener.html) class that defines the action to take when the user presses the button:

```java
        alertDialog.setPositiveButton("Ok", new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialog, int which) {
               // User clicked OK button.
              // ... Action to take when OK is clicked.
            }
        });
        alertDialog.setNegativeButton("Cancel", new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialog, int which) {
                // User clicked the CANCEL button.
               // ... Action to take when CANCEL is clicked.
            }
        });
```

You can add only one of each button type to an _AlertDialog_. For example, you can't have more than one "positive" button.

**Tip**: You can also set a "neutral" button with [setNeutralButton()](https://developer.android.com/reference/android/app/AlertDialog.Builder.html#setNeutralButton(int,%20android.content.DialogInterface.OnClickListener)). The neutral button appears between the positive and negative buttons. Use a neutral button, such as **Remind me later**, if you want the user to be able to dismiss the dialog and decide later.

### Displaying the dialog

To display the dialog, call its show() method:

```java
alertDialog.show();
```

## Date and time pickers

Android provides ready-to-use dialogs, called _pickers_, for picking a time or a date. Use them to ensure that your users pick a valid time or date that is formatted correctly and adjusted to the user's locale. Each picker provides controls for selecting each part of the time (hour, minute, AM/PM) or date (month, day, year).

<br>
<p align="center">
<img  src="https://github.com/saisankar12/document/blob/master/saisankar_concept_images/pickers_output.png">
</p>
<br>

