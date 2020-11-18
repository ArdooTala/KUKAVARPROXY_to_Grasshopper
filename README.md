# KUKAVARPROXY_to_Grasshopper
A simple grasshopper plugin for online-control of a KUKA (KRC2/4) by modifying global Variables from Grasshopper using KUKAVARPROXY.

---

### SETUP AND INSTALL
#### Robot-Controller
Download KUKAVARPROXY from it's [Github page](https://github.com/ImtsSrl/KUKAVARPROXY).

> **Warning**: Changing the arm's ip address will break the connection between the controller and the arm. Proceed with caution.

#### Grasshopper
Download the `KukaVP_GH.ghpy` file and simply drag and drop to Grasshopper or copy to the Grasshopper's components folder.

**Components folder default path**  
`C:\ProgramData\Roaming\Grasshopper\components`

**OR**  
In Grasshopper go to  
`File > Special Folders > Components**`

---

### USAGE
KUKAVARPROXY should be running on the robot controller and the robot should be connected to the computer. The connection is recommended to be tested by (as described in the troubleshooting section > Testing the communication) before using the plugin.

The communication is established using the `Robot` component in the grasshopper. The output of the component is then used as the input for the `Read` and `Write` components.

> By default, KUKAVARPROXY will terminate the communication after 30 seconds of inactivity. The `Read` and `Write` components will re-establish the communication if needed. However, re-establishing the communication will cause a delay in communicating the data. If this delay is a problem, in order to prevent the termination of the communication, the `KeepAlive` component can be used. This component keeps sending data over the network every 25 seconds to prevent the communication from terminating.

#### Components
- ##### Robot
Use the `Robot` component to connect to the robot.
    - ###### Inputs
        - **IP:** text containing the IP of the robot. example: `192.168.1.100`
        - **Connect:** Boolean whether to establish to connection or not.
    - ###### Outputs
        - **Robot:** The *Robot* object to use with other components.

- ##### Read
    - ###### Inputs
        - **Robot (ROB):** The **Robot** output from the **Robot** component.
        - **Variable (VAR):** Boolean whether to establish to connection or not.
    - ###### Outputs
        - **Value (VAL):** The Value of the Variable in the robot.

- ##### Write
    - ###### Inputs
        - **Robot (ROB):** The **Robot** output from the **Robot** component.
        - **Variable (VAR):** Variable to write to.
        - **Value (VAL):** The value to write to the defined variable.
        - **Write (WR):** Boolean to write to the robot.
    - ###### Outputs
        - **Done (OK):** Boolean defining if the write is done.

- ##### Keep Alive
    - ###### Inputs
        - **Robot (ROB):** The **Robot** output from the **Robot** component.
        - **Keep (ALV):** Boolean whether to keep the connection alive or not.

---

###### Variables List

###### Troubleshooting
