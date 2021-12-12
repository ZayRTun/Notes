- [Home](../index.md)
---
# Flutter Drawer Codes

```dart
import 'package:flutter/material.dart';

class DrawerSample extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      drawer: Drawer(),
      body: Builder(builder: (BuildContext context) {
        return GestureDetector(
          child: Icon(
            Icons.menu,
            size: 30.0,
            color: Color(0xff3830A1),
          ),
          onTap: () {
            Scaffold.of(context).openDrawer();
          },
        );
      }),
    );
  }
}
```