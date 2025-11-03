ZMK Module for the <s>lovely</s> Pain27 keyboard by uuupah: https://github.com/uuupah/pain27_kb

To be honest, i'm not sure if the leds are configured right, that'll have to wait until I build my board.

To include the module add the marked lines (>) to your zmk-config/config/west.yml:

    manifest:
      defaults:
        revision: v0.3
      remotes:
        - name: zmkfirmware
          url-base: https://github.com/zmkfirmware
    >    - name: pain27_shield_module
    >      url-base: https://github.com/devilzmods/
        # Additional modules containing boards/shields/custom code can be listed here as well
        # See https://docs.zephyrproject.org/3.2.0/develop/west/manifest.html#projects
      projects:
        - name: zmk
          remote: zmkfirmware
          import: app/west.yml
    >    - name: pain27_shield_module
    >      remote: pain27_shield_module
    >      revision: main
      self:
        path: config

zmk-config/build.yml should look like this:

    ---
    include:
      - board: nice_nano_v2 #your controller of choice
        shield: pain27
