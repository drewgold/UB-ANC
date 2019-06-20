## UB-ANC Agent API Information

[MAVLink Common Message Set] (https://mavlink.io/en/messages/common.html)

[Copter commands in Guided Mode] (http://ardupilot.org/dev/docs/copter-commands-in-guided-mode.html)

[QGeoCoordinate] (http://doc.qt.io/archives/qt-5.7/qgeocoordinate.html#QGeoCoordinate)

[Vehicle]  (https://github.com/mavlink/qgroundcontrol/blob/Stable_V3.2/src/Vehicle/Vehicle.h)


* ###### Get the current position of the drone (QGeoCoordinate):
```C++
        QGeoCoordinate gps_pos;
        gps_pos = m_mav->coordinate();
```

* ###### Altitude:
```C++
        double alt;
        alt = m_mav->altitudeRelative()->rawValue().toDouble();
```

* ###### Latitude:
```C++
        double lat;
        lat = m_mav->coordinate().latitude();
```

* ###### Longitude:
```C++
        double lon;
        lon = m_mav->coordinate().longitude();
```

* ###### Check if in guided mode:
```C++
        m_mav->guidedMode();
```

* ###### Takeoff to TAKEOFF_ALT:
```C++
        m_mav->sendMavCommand(m_mav->defaultComponentId(),
                        true,
                        true, // show error
                        0.0f, 0.0f, 0.0f, 0.0f, 0.0f, 0.0f,
                        TAKEOFF_ALT);
```

* ###### Takeoff to 2.5 meters:
```C++
        m_mav->guidedModeTakeoff();
```

* ###### Get vehicle ID:
```C++
        int id;
        id = m_mav->id();
```

* ###### Check if vehicle is armed:
```C++
        bool armed;
        armed = m_mav->armed();
```

* ###### Arm the vehicle:
```C++
        m_mav->setArmed(true);
```

* ###### Define new GPS coordinate based on current coordinate and desired distance and azimuth:
```C++
        QGeoCoordinate new_gps;
        new_gps = m_mav->coordinate().atDistanceAndAzimuth(10, 90);
        // Note: Azimuth 0 is North, 90 is East
```

* ###### Go to location (overwriting current target):
```C++
        QGeoCoordinate dest;
        m_mav->guidedModeGotoLocation(dest);
```

* ###### Figure out distance to another coordinate:
```C++
        QGeoCoordinate dest; // need to assign some dest
        qreal dist;
        qreal azimuth;
        dist = m_mav->coordinate().distanceTo(dest);
        azimuth = m_mav->coordinate().azimuthTo(dest);
```

* ###### Set to land mode:
```C++
        m_mav->guidedModeLand()
```
