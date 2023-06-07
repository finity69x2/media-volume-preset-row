# THIS IS A WORK IN PROGRESS. DON"T USE IT YET!!!


# media-volume-preset-row
Provides a means to program 4 preset volume settings for media entities selectable from a Lovelace button row. This plugin will also accept a "media group" as the entity_id.

This element is completely theme-able to provide a match to the other control rows to provide a consistent look for the different elements in your Lovelace frontend

Installation:

The easiest way to install this is to use the Home Assistant Community Store (HACS) in Home Assistant.

Follow the instructions there for installation making sure you note the "url:" section for the resources addition.


Conversely, if you don't use HACS you can install it manually by performing the following:

Copy the media-volume-preset-row.js file to the appropriate folder in your Home Assistant Configuration directory (/config/www/).

Place the following in your "resources" section in your lovelace configuration (updating the localation to where you placed the above file):

  ```
    - url: /local/media-volume-preset-row.js
      type: module
  ```
    
Then to use this in a card place the following in your entity card:


<b>Options:</b>

| Name | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| type | String | Yes | none | custom:media-volume-entity-row |
| entity | String | Yes | none | Any media entity_id (including "media group" entities) |
| name | String | No | none | A custom name for the entity in the row |
| customSetpoints | Boolean | No | false | Set to true to use custom volume setpoints |
| customTheme | Boolean | No | false | Set to true to use a custom theme |
| customText | Boolean | No | false | Set to true to use custom button text |
| reverseButtons | Boolean | No | false | Set to true to reverse the button order |
| allowDisablingButtons | Boolean | No | true | Set to false to prevent buttons being disabled |
| width | String | No | 30px | A custom width for the buttons |
| height | String | No | 30px | A custom height for the buttons |
| maxVolume | Integer | No | 99 | Sets the volume setpoint for the "max" button (max 100) |
| midMaxVolume | Integer | No | 66 | Sets the volume setpoint for the "mid max" button  |
| midMinVolume | Integer | No | 33 | Sets the volume setpoint for the "mid min" button |
| minVolume | Integer | No | 0 | Sets the volume setpoint for the "min" button (min 0)|
| isMaxColor | String | No | '#f44c09' | Sets the color of the 'max' button if the volume is at that setpoint |
| isMidMaxColor | String | No | '#f44c09' | Sets the color of the 'mid max' button if the volume is at that setpoint |
| isMidMinColor | String | No | '#f44c09' | Sets the color of the 'mid min' button if the volume is at that setpoint |
| isMinColor | String | No | '#43A047' | Sets the color of the 'min' button if the volume is at that setpoint |
| buttonInactiveColor | String | No | '#759aaa' | Sets the color of the the buttons if that selection is not "active" |
| customMaxText | String | No | '99%' | Sets the text of the "max" volume button |
| customMidMaxText | String | No | '66%' | Sets the text of the "mid max" volume button |
| customMidMinText | String | No | '33%' | Sets the text of the "mid min" volume button |
| customMinText | String | No | '0%' | Sets the text of the "min" volume button |
| state_color | Boolean | No | false | Sets the icon color of the entity to reflect the current state |


The values for the colors can be any valid color string in "HEX", "RGB" or by color name.

If no custom setting is provided it will use the 'default' value for that individual setting.

If the media player volume is changed via any other means (slider, service call, etc) the buttons will indicate which range the media player volume is in based on the setpoint settings in the config.

This plugin can also be used with a group of media players by creating a "media player group". Then each media player in the group will be simultaneously controlled by the plugin.

<b>Configuration Examples:</b>
    
  ```
    cards:
      - type: entities
        title: cover theme test
        show_header_toggle: false
        state_color: true
        entities:
          - type: custom:cover-position-preset-row
            name: Blind Custom Position
            entity: cover.blinds_test
            reverseButtons: true
            ## used to select your own customizable theme
            customTheme: true
            isOpenedColor: 'rgb(255, 0, 0)'
            isMidOpenedColor: '#888888'
            isMidClosedColor: '#222222'
            isClosedColor: 'purple'
            buttonInactiveColor: 'black'
            ## used to set the custom setpoints for the cover (default is 0, 33, 66, and 99)
            customSetpoints: true
            openPosition: 85
            midOpenPosition: 40
            midClosePosition: 20
            closePosition: 8
            ## used to select custom text for the buttons (defaults to 0, 33, 66, 99. Or it defaults to the values of the setpoints if custom setpoints are used)
            customText: true
            customOpenText: open
            customMidOpenText: mop
            customMidClosedText: mcls
            customClosedText: cls
            width: '15px'
            height: '15px'
  ```

This is with the default Lovelace frontend theme set:

![Default](blinds_default.jpg)


This is with the "Slate" frontend theme set:

![Slate](blinds_default_slate_theme.jpg)

This is with custom setpoints and a custom theme:

![Custom Setpoints and Theme](blinds_custom_setpoints.jpg)

And here is the above with custom text:

![Custom Setpoints and Theme](blinds_custom_text.jpg)
