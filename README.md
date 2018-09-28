  - alias: Iluminação Sala
    initial_state: true
    trigger:
      platform: state
      entity_id: binary_sensor.motion_sensor_158d0001f9d417
      to: 'on'
    condition:
        - condition: and
    conditions:
        - condition: time
          after: '18:00:00'
          before: '22:00:00'
        - below: '100'
          entity_id: sensor.illumination_7811dcb38555
          platform: numeric_state
          value_template: '{{ states(“sensor.illumination_7811dcb38555”) }}'
    action:
      - service: light.turn_on
        data_template:
          entity_id: group.sala
          brightness: 100
          color_name: aqua
