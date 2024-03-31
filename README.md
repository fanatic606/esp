# esp

https://mermaid.live/edit#pako:eNqNVG1P2zAQ_itWPpOGhqFJ_TAJBpPYystoh6alqHIdp_HwS3AuDRPl8_7YftjOiRO1pUJUaeLcc77n7nxPngNmUh6MgkyamuXUAhnfzjTBX5HcCQbWaHKTG67FExnGUXx8eN_Ctocvb26m5ONxNDz2kOyhU1nxiXJRh_EKHU68h0mmtlKUfDZqIcgHEhJxxYH89DAvi6M4ae7ewqRgD62d5JZnZBbkAEU5iiI05kbxgTDRshIpL6MlBxB6OS8BmXk6Z0YpqtO5FJoPclByFuB-oRGXlP2ms8CXFJZCJdZUwJtlV2no4nd2t_aArliCf1Iwb1CPj5C4Gym5XXEbZcKqmlq-VUXjsFNEXdcDFzmkZSkwLw2uHqGBLy0FYXQZqUeAqMk8NW3upqaM1MTtI_2-rpicJtvA_mRy-t5UHKNscokcRxtkxZO788GZsJxBfPl9Ot3PsuK7LEsBebUY4NFEt1RmX8fRdhxfKFb_7y8BQ7qyRJzgKcLCPMVNQ_bSifgNOsUOh8PDaDNKQzbNRUnwokhnJIiCZMbiG07NQ8euh8l7C-hmJE7el0Pnf7TP_wtdCKrDCcuVSKEb-RCciOY-yr07kzZIWS2wcUVOTn5Mr72aSRh-Wt-dk8KQB7qQ1dqryc_427DcgE_H59ugacBWwHsd2rVzwjlgRqMyYI0zsYv6EL2H6ALgNoe7Nq0bZXazsNfMddo1orH2TsTpyWK31l7Tr_p1dn25qXm306m8eTaydYucvuIBLnmG37tNWNICTNGbdpjGF1ffLjqrHrZMcfs46uMHB4HiVlGR4if62ZlnAeQcMw9GTh88o5VsJP-CrrQCM_mjWTDCweAHQVWkFPiZoEipglFGZYnWgupfxnTvL_8BO9r6eQ

https://community.victronenergy.com/questions/184828/reading-victron-ble-broadcasts-with-arduino-esp32.html

https://community.victronenergy.com/questions/53269/vedirect-to-mqtt-gateway-using-esp32.html



bla bla bla
https://esphome.io/guides/getting_started_command_line.html

https://www.home-assistant.io/integrations/mqtt/

https://www.home-assistant.io/installation/

https://github.com/RalfJL/VE.Direct2MQTT

https://github.com/mc0110/inetbox2mqtt

https://github.com/Fabian-Schmidt/esphome-truma_inetbox



```mermaid
flowchart LR
    p[Victron Phoenix 12/250]
    r[Victron MPPT 75/15]
    l[Victron BlueSmart 12v/15A]
    o[Truma Combi 4 - iNet X]
    esp32[esp32]
    click esp32 href "https://esphome.io/guides/getting_started_command_line.html" "instalacja"
    r-sim[router-sim]
    r-home[router-home]
    nuc[nuc pc]
    mqqt[mqqt server/firmware]
    click mqqt href "https://www.home-assistant.io/integrations/mqtt/" "doinstalowac w home assistant"
    ha[home assistant/firmware]
    click ha href "https://www.home-assistant.io/installation/"

    ve[VE.Direct2MQTT/firmware]
    click ve href "https://github.com/RalfJL/VE.Direct2MQTT" "dograć to "
    i2[inetbox2mqtt/firmware]
    click i2 href "https://github.com/mc0110/inetbox2mqtt" "This is a tooltip for a link"
    n1[https://github.com/RalfJL/VE.Direct2MQTT]
    n2[https://github.com/mc0110/inetbox2mqtt]
    n3[https://github.com/Fabian-Schmidt/esphome-truma_inetbox]


    subgraph AUTO
    p -->|VE po kablu| esp32 
    r -->|VE po kablu| esp32 
    l -->|VE po BLE| esp32 
    o -->|iNet X po BLE| esp32 
    esp32 -->|ve convert| ve
    esp32 -->|iNet X convert| i2 
    ve -->|mqtt|r-sim
    i2 -->|mqtt|r-sim
    end

    r-sim -->|mqtt internet| r-home

    subgraph DOM
    r-home --> nuc --> mqqt --> ha
    end

    telefon --> ha
    laptop --> ha

    subgraph LINKI

    n1 --> n2 --> n3
    end
```
