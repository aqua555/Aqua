import 'package:flutter/material.dart';

void main() { runApp(AquaPrimApp()); }

class AquaPrimApp extends StatelessWidget { @override Widget build(BuildContext context) { return MaterialApp( title: 'Aqua Prim', debugShowCheckedModeBanner: false, theme: ThemeData( primarySwatch: Colors.teal, fontFamily: 'Tajawal', ), home: LoginScreen(), ); } }

class LoginScreen extends StatefulWidget { @override _LoginScreenState createState() => _LoginScreenState(); }

class _LoginScreenState extends State<LoginScreen> { final _formKey = GlobalKey<FormState>(); String _email = ''; String _password = '';

@override Widget build(BuildContext context) { return Scaffold( body: Center( child: Padding( padding: const EdgeInsets.symmetric(horizontal: 24.0), child: Form( key: _formKey, child: Column( mainAxisSize: MainAxisSize.min, children: [ Text( 'تسجيل الدخول', style: TextStyle( fontSize: 28, fontWeight: FontWeight.bold, color: Colors.teal[700], ), ), SizedBox(height: 24), TextFormField( decoration: InputDecoration( labelText: 'البريد الإلكتروني', border: OutlineInputBorder(borderRadius: BorderRadius.circular(8)), ), keyboardType: TextInputType.emailAddress, validator: (value) { if (value == null || value.isEmpty) { return 'يرجى إدخال البريد الإلكتروني'; } return null; }, onSaved: (value) => _email = value!, ), SizedBox(height: 16), TextFormField( decoration: InputDecoration( labelText: 'كلمة المرور', border: OutlineInputBorder(borderRadius: BorderRadius.circular(8)), ), obscureText: true, validator: (value) { if (value == null || value.isEmpty) { return 'يرجى إدخال كلمة المرور'; } return null; }, onSaved: (value) => _password = value!, ), SizedBox(height: 24), ElevatedButton( style: ElevatedButton.styleFrom( padding: EdgeInsets.symmetric(horizontal: 48, vertical: 12), shape: RoundedRectangleBorder( borderRadius: BorderRadius.circular(8), ), ), onPressed: () { if (_formKey.currentState!.validate()) { _formKey.currentState!.save(); // TODO: implement Firebase Auth login } }, child: Text( 'دخول', style: TextStyle(fontSize: 18), ), ), ], ), ), ), ), ); } }

