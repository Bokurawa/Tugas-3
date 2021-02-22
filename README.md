# Tugas-3

import 'package:flutter/material.dart';
​
void main() => runApp(MyApp());
​
class MyApp extends StatelessWidget {
  Widget build(BuildContext context) {
    return MaterialApp(
      
      home: Scaffold(
        
        appBar: AppBar(title: Text('Shauma Akbari - 5SIA2')),
        
        body: Shauma(),
      ),
    );
  }
}
​
class Jurusan {
  const Jurusan(this.kode, this.namajurusan);
​
  final String namajurusan;
  final String kode;
}
​
class Shauma extends StatefulWidget {
  _Shauma createState() => new _Shauma();
}
​
class _Shauma extends State<Shauma> {
  Jurusan pilihjur;
  List<Jurusan> jurusan = <Jurusan>[
    const Jurusan('SI', 'Sistem Informasi'),
    const Jurusan('MI', 'Manajemen Informatika')
  ];
​
  void initState() {
    pilihjur = jurusan[0];
  }
​
  Widget build(BuildContext context) {
    return Container(
      padding: EdgeInsets.all(20.0),
      child: Column(
        children: <Widget>[
          TextField(
            decoration: InputDecoration(labelText: "Input Nama Mahasiswa"),
          ),
          DropdownButton<Jurusan>(
            isExpanded: true,
            value: pilihjur,
            onChanged: (Jurusan newValue) {
              setState(() {
                pilihjur = newValue;
              });
            },
            items: jurusan.map((Jurusan jurusan) {
              return new DropdownMenuItem<Jurusan>(
                value: jurusan,
                child: Text(jurusan.namajurusan),
              );
            }).toList(),
          ),
          Text("${pilihjur.namajurusan} dengan kode ${pilihjur.kode}"),
        ],
      ),
    );
  }
}
