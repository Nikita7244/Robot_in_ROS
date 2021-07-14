import PySimpleGUI as sg
import paho.mqtt.client as mqtt # import the client1

broker_address="localhost" # use external broker
client = mqtt.Client("P1") # create new instance
client.connect(broker_address) # connect to broker
sg.set_options(element_padding=(0, 0))

layout = [ [sg.Button("End of session"), sg.Button("Malii vpered"), sg.Button("Malii nazad"), sg.Button("Stop machina")],[sg.Button("Nalevo"), sg.Button("Napravo")]]
 # Create the window
window = sg.Window("Robot GUI", layout,
          default_element_size=(12, 1),
          auto_size_text=False,
          auto_size_buttons=False,
          default_button_element_size=(15, 2),
	  finalize=True)
window.bind('<Key-w>', 'w')
window.bind('<Key-a>', 'a')
window.bind('<Key-s>', 's')
window.bind('<Key-d>', 'd')
window.bind('<Key-x>', 'x')
# Create an event loop
while True:
    event, values = window.read()
 	
    if event == "Malii vpered" or event == 'w':
    	client.publish("turtle",'{"linear":{"x": 0.1, "y": 0.0, "z": 0.0}}')
    if event == "Stop machina" or event == 'x':
    	client.publish("turtle",'{"linear":{"x": 0.0, "y": 0.0, "z": 0.0}}')  
    if event == "Malii nazad"  or event == 's':
    	client.publish("turtle",'{"linear":{"x": -0.1, "y": 0.0, "z": 0.0}}')
    if event == "Nalevo" or event == 'a':
    	client.publish("turtle",'{"angular":{"x": 0.0, "y": 0.0, "z": 0.2}}') 
    if event == "Napravo" or event == 'd':
    	client.publish("turtle",'{"angular":{"x": 0.0, "y": 0.0, "z": -0.2}}')  	
    if event == "End of session" or event == sg.WIN_CLOSED:
        break
window.close()

