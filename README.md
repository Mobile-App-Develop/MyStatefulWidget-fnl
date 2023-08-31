import 'package:flutter/material.dart';

// stateful widgets: have multiple states
// **All flutter widgets are immutable:**
// All programming languages believe in immutability
//

// mutable: Changeable
// immutable: not-changeable

void main() {
  runApp(
    MyStatefulWidget(),
  );
}

// stateful widget
class MyStatefulWidget extends StatefulWidget {
  const MyStatefulWidget({super.key});

  @override
  State<MyStatefulWidget> createState() => _MyStatefulWidgetState();
}

// its state class
class _MyStatefulWidgetState extends State<MyStatefulWidget> {
  String text = "ABC";

  @override
  Widget build(BuildContext context) {
    debugPrint("build");
    TextEditingController _controller = TextEditingController();
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(
          title: Text("Stateful Widget"),
        ),
        body: Material(
          child: Container(
            margin: EdgeInsets.all(20),
            child: Column(
              children: [
                TextField(
                  controller: _controller,
                  keyboardType: TextInputType.name,
                  decoration: InputDecoration(
                    hintText: "Introduction",
                    label: Text(
                      "Enter intro",
                      style:
                          TextStyle(fontSize: 20, fontWeight: FontWeight.bold),
                    ),
                    border: OutlineInputBorder(),
                  ),
                ),
                Padding(
                  padding: const EdgeInsets.all(8.0),
                  child: ElevatedButton(
                    onPressed: () {
// Most important function in stateful widget
                      setState(() {
                        text =
                            _controller.text; // it will fetch textfield's data
                      });
                    },
                    child: Text("Show data"),
                  ),
                ),
                Padding(
                  padding: const EdgeInsets.all(8.0),
                  child: Text(text),
                )
              ],
            ),
          ),
        ),
      ),
    );
  }
}

// Assignment:
// Flutter's Project Structure
// Stateless & Stateful Widgets, setState( )
// Navigations
