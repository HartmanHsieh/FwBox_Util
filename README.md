# FwBoxLiteJson
Very tiny json parser. It can't pasrse full tree, can only search for the key and get it's value.

Example:
```cpp
void loop() {
  // put your main code here, to run repeatedly:
  FwBoxLiteJson lj;
  
  String str_json = "{\"Name\":\"John\",\"Age\":18,\"Phone\":\"0900111222\",\"TEST\":[\"AA\",\"BB\",\"CC\"]}";

  Serial.println(str_json);

  int temp_i = 0xfe;
  if (lj.getInt(&str_json, "Age", &temp_i) == 0) { // success
    Serial.print("Age = ");
    Serial.println(temp_i);
  }

  String temp = "";
  if (lj.getString(&str_json, "Phone", &temp) == 0) { // success
    Serial.print("Phone = ");
    Serial.println(temp);
  }

  String temp_arr[5];
  temp_i = 5;
  if (lj.getArrayString(&str_json, "TEST", temp_arr, &temp_i) == 0) { // success
    Serial.print("Array Count = ");
    Serial.println(temp_i);
    for(int ii = 0; ii < temp_i; ii++) {
      Serial.print("TEST[");
      Serial.print(ii);
      Serial.print("] = ");
      Serial.println(temp_arr[ii]);
    }
  }

  Serial.println();

  delay(10 * 1000);
}
```

