---
layout: entry
title:  "Link"
categories: controls
order: 1

keyboard:
  tab: |
    Focus visibly moves to the link
  spacebar: |
    Activates the link on iOS and Android
  enter: |
    Activates the link on Android
          
mobile:
  swipe: |
    Focus moves to the element
  rotor: |
    Can be used to navigate to and activate links 
  doubletap: |
    Activates the link

screenreader:
  name:  |
    Purpose and destination is clear
  role:  |
    Identifies itself as a link
  group: |
    n/a
  state: |
    Expresses its state if applicable (disabled/dimmed)
---


## Developer notes

- Clickable textview that navigates the user outside the app (Ex: to a browser)

### Name

- Clickable text describes the destination or purpose of the link.

### Role

- Ensure links appear in the Local Context Menu and Rotor
- Ensure links can be activated from text view or from the LCM or Rotor. Only one way is required
  
- **iOS  
  **
  - Use `TextView` with `UIAccessibilityTraitLink`. Announces as "link"
- **Android**  
  - `TextView` - Announces as "link"  
  - `URLSpan` / `ClickableSpan`
  - Linkify Class

### Groupings

- Link text can be grouped with paragraph text to make a larger touch target, provided there is only one interactive link in group.

### State

- **iOS**
  - Active: `isEnabled property`
  - Disabled: `UIAccessibilityTraitNotEnabled`. Announcement: dimmed  
- **Android**  
  - Active: `android:enabled`
  - Disabled: `android:enabled`. Announcement: disabled

### Focus

- Only manage focus when needed. Primarily, let the device manage default focus.  
  
- **iOS Options**
  - `accessibilityElementIsFocused`  
  - `isAccessibilityElement` makes the element visible or not to the Accessibility API
  - `accessibilityElementsHidden` indicates that the children elements of the target element are visible or not to the Accessibility API
  - To move screen reader focus to newly revealed content: `UIAccessibilityLayoutChangedNotification`
  - To NOT move focus, but announce new content: `UIAccessibilityAnnouncementNotification`
- **Android Options**
  - `android:focusable`
  - `android=clickable`
  - Implement an `onClick( )` event handler for keyboard, as well as `onTouch( )`
  - `nextFocusDown`
  - `nextFocusUp`
  - `nextFocusRight`
  - `nextFocusLeft`
  - `accessibilityTraversalBefore` (or after)
  - To move screen reader focus to newly revealed content: `Type_View_Focused`
  - To NOT move focus, but announce new content: `accessibilityLiveRegion` (set to polite or assertive)
  - To hide controls from screen reader: `Important_For_Accessibility_false`
