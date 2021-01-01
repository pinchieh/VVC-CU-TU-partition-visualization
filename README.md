# VVC-CU/TU-partition-visualization
# Visualization  
![image](https://github.com/pinchieh/Two-phase-Multi-model/blob/master/Fast%20QTMT%20Alg.PNG)
# Visualize CU/TU partition  
Add the following code in EncCU.cpp at the end of compressCTU function  
### CU
  
```
  string filename = to_string(ctuindex);
  ofstream myfile;
  myfile.open("./CTU_" + filename + ".txt");
  for (auto &currCU : cs.traverseCUs(area, CH_L))
  {
	  const CompArea&  lumaArea = currCU.block(COMPONENT_Y);
	  int cuX = lumaArea.x;
	  int cuY = lumaArea.y;
	  int cuH = lumaArea.height;
	  int cuW = lumaArea.width;
	  string info = "";


	  info = to_string(cuX) + " " + to_string(cuY) + " " + to_string(cuH) +" "+ to_string(cuW) +"\n";
	  myfile << info;


  }

  myfile.close();
```

### TU
  
```  
  ofstream TUmyfile;
  TUmyfile.open("./TU_" + filename + ".txt");
  for (auto &currCU : cs.traverseCUs(area, CH_L))
  {
	  for (auto &currTU : CU::traverseTUs(currCU))
	  {

		  const CompArea&  lumaArea = currTU.block(COMPONENT_Y);
		  int cuX = lumaArea.x;
		  int cuY = lumaArea.y;
		  int cuH = lumaArea.height;
		  int cuW = lumaArea.width;
		  int mtsidx = currTU.mtsIdx;
		  string info = "";
		  info = to_string(cuX) + " " + to_string(cuY) + " " + to_string(cuH) + " " + to_string(cuW) + " " + to_string(mtsidx) + "\n";
		  TUmyfile << info;

	  }

  }

  TUmyfile.close();
```
