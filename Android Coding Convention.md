# Project guidelines
## File naming
### Class files
Class names are written in TextCapWords: capitalize the first character of every word. <br />
Example: SignInActivity, SignInFragment...
### Resource files
Resource file names are written in lowercase_underscore. <br /><br />
__*Drawable files*__: start with acronym of asset type:

|Asset Type| Prefix |Example|
|----------|--------|-------|
|Button    |button_ |button_send_normal.png|
|Dialog    |dialog_ |dialog_title.png|
|Icon      |icon_     |icon_star.png|
|Tab Icon  |icon_tab_ |icon_tab_recent.png|
|Menu      |menu_   |menu_background.png|

Naming convention for selector states:

| State   | Suffix | Example |
|---------|--------|---------|
| normal  |  _normal | button_send_normal.png |
| pressed | _pressed | button_send_pressed.png |
| focused | _focused | button_send_focused.png |
| selected | _selected | button_send_selected.png |

__*Layout file*__: should match the name of Android component that they are intented for.

| Component | Class name | Layout name |
|-----------|------------|-------------|
| Activity  | SignInActivity | activity_sign_in.xml |
| Fragment  | SignUpFragment | fragment_sign_up.xml |
| Dialog    | ChangePasswordDialog | dialog_change_password.xml |

Different case is when we create a layout that are intended to be a part of other layout,
or create a layout that is going to be inflated by an Adapter:

| Component | Layout name |
|-----------|-------------|
|AdapterView Item | item_user_profile.xml |
|Partical Layout | layout_user_info.xml |

# Code guidelines
## Use javadoc standard comments
Every class or nontrivial pubic method you write must containt a Javadoc comment with at least one sentence describing what method does. 
This sentence should start with a third person descriptive verb.

```
/**
* Class description
*/
public class Foo {
  ...
}
```
or
```
/**
* Return the correctly rounded positive square root of a double value.
*/
public double sqrt(double a) {
  ...
}
```
You don’t need to write Javadoc for trivial method such as get and set method (setFoo(), getFoo()…).
If the method does something more complex then you must document it.

## Write short method
Keep method small, and focused.
## Define fields
Define fields either at the top of the file or immediately before the methods that use them.
## Naming convention
*	Public static final field (constants) are `ALL_CAP_WITH_UNDERSOCRES`.
* Non-public, non-static field name start with `m`.
*	Static field name start with `s`.
*	Other fields start with `a lower case letter`.
```
public class MyClass {
  public static final int SOME_CONSTANT = 42;
  public int publicField;
  private static MyClass sSingleton;
  int mPrivateField;
  protected int mProtectedField;
}
```
Many elements of Android SDK such as SharedPreferences, Bundle, or Intent use a key-value pair. 
When using one of these components, you must define the keys as a static final fields and they should be prefixed as indicated below.

| Element | Prefix |
|---------|--------|
|SharedPreference | PREF_ |
|Bundle | BUNDLE_ |
|Argument| ARGS_ |

When data type of variables is a View components, they should be suffixed with their data type.

```
  private TextView mUserNameTextView;
  public Button mDeleteButton;
```
## Treat acronyms as word
Treat Acronyms and abbreviations as words in naming variables, methods and classes to make names more readable:

| Good | Bad |
|------|-----|
|XmlHttpRequest | XMLHTTPRequest |
|getCustomerId | getCustomerID |
|String url | String URL |
| long id | long ID |

## Use standard brace style
Braces do not go in their own line, they go on same line as the code before them:
```
class MyClass {
  int func() {
    if (something) {
      //...
    } else {
      //...
    }
  }
}
```
Exception: If the entire conditional fit on one line, you may (but are not obligated to) put it all on one line. Example: <br />
You should use:

```
if (condition) {
  body();
}
```

or 

```
if (condition) body();
```

but not use:

```
if (condition)
  body();
```

## Line length limit

**_Break at operators_**: When the line break at an operator, the break come before the operator.

```
int longName = anotherVeryLongVariable + anEvenLongerOne - thisRidiculousLongOne
      + theFinalOne;
```

or the line can be break after operator `=`

```
int longName = 
      anotherVeryLongVariable + anEvenLongerOne - thisRidiculousLongOne + theFinalOne;
```

__*Method chain case*__: When multiple methods are chained in the same line, every mothod should go in its own line, breaking the line before.

```
Picasso.with(context)
        .load(url)
        .into(imageView);
 ```
 
__*Long parameters case*__: When a methods has many parameters or its parameter are very long, we should break the line after every `,`

```
loadImage(context,
          "http://develop.com/images/arsenal_logo.png",
           mTeamLogoImageView,
           clickListener,
           "Arsenal Title");
```

## XML style rules
### Use self closing tab
When an XML element doesn’t have any content, you must use self closing tab:
 
```
<TextView
   android:id="@+id/text_name"
   android:layout_width="wrap_content"
   android:layout_height="wrap_content" />
```
 
### Resource naming
__*Id naming*__: Ids should be prefixed with the name of the element in lowercase_underscore.
 
| Element | Prefix | Example |
|---------|--------|---------|
| TextView | text_ | text_user_name |
| Button | button_ | button_save|
| ImageView | image_ |image_user_picture|
| Menu | menu_ | menu_setting|
| EditText | edit_ |edit_user_email|
| LinearLayout, FrameLayout... | layout_ | layout_user_info|
| ListView | list_ | list_user|
 
__*Strings*__:
  * String name start with a prefix that identifies the section they belong to. <br />
  Example: sign_in_email_hint, sign_in_title...
  * If a string doesn't belong to any section, it should be prefixed  with the name of element. Example:
    
  |Prefix|Description|
  |------|-----------|
  | error| An error message|
  | msg_ | A regular information message |
  
  * restrict use the same string for different views. 
