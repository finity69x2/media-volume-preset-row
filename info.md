Provides a means to program 3 preset position settings for programmable cover entities selectable from a Lovelace button row. THis plugin will also accept a "cover group" as the entity_id.

This pluig-in was inspired by user @ktownsend-personal  on the Home Assistant forum (community.home-assistant.io) as a thematically complementary plug-in for my other various control rows.

This element is completely theme-able to provide a match to the other control rows to provide a consistent look for the different elements in your Lovelace frontend

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
            isOpenColor: 'rgb(255, 0, 0)'
            isMidOpenColor: '#888888'
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
  ```

This is with the default Lovelace frontend theme set:

![Default](blinds_default.jpg)


This is with the "Slate" frontend theme set:

![Slate](blinds_default_slate_theme.jpg)

This is with custom setpoints and a custom theme:

![Custom Setpoints and Theme](blinds_custom_setpoints.jpg)

And here is the above with custom text:

![Custom Setpoints and Theme](blinds_custom_text.jpg)
