import Adafruit_BBIO.GPIO as GPIO
import Adafruit_BBIO.ADC as ADC
import time
import numpy as nm

ADC.setup()
test = 1

n_samp = 5000

bvolt = nm.zeros((n_samp,1))
tvolt = nm.zeros((n_samp,1))

for i in range(n_samp):
	value1 = ADC.read("AIN4")
	voltage1 = value1 * 1.8

	time.sleep(0.001)
	value2 = ADC.read("AIN5")
	voltage2 = value2 * 1.8

	print(voltage1)
	if voltage1 > 0.8:
		print "Biceps Contraction"
	if voltage2 > 0.8:
		print "Triceps Contraction"
	bvolt[i] = voltage1
	tvolt[i] = voltage2
	
	time.sleep(0.001)

#nm.savetxt('emg_data_biceps',bvolt);
#nm.savetxt('emg_data_triceps',tvolt);

f = open('emg_data','w')
f.write("\n".join([",".join([str(n) for n in item]) for item in bvolt]))
f.write("\n".join([",".join([str(n) for n in item]) for item in tvolt]))
f.close()
