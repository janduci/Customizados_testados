import paramiko
import time
ssh_client = paramiko.SSHClient()
ssh_client.set_missing_host_key_policy(paramiko.AutoAddPolicy())

# creating a dictionary for each device to connect to
disp1 = {'hostname': 'coreeabrspjucpd01', 'port': '22', 'username':'adm-aj7817', 'password':'senhaqui'}

# creating a list of dictionaries (of devices)
dispositivos = [disp1, disp2, disp3, disp4, disp5, disp6, disp7, disp9, disp10, disp11, disp12, disp13, disp14, disp16, disp17, disp18, disp19, disp20, disp21, disp23, disp24, disp26, disp27, disp28, disp29, disp30, disp31, disp32, disp33, disp34, disp35]

# iterating over the list (over the devices) and backup the config
for disp in dispositivos:
    print(f'Connecting to {disp["hostname"]}')
    ssh_client.connect(**disp, look_for_keys=False, allow_agent=False)
    shell = ssh_client.invoke_shell()

    shell.send('enable\n')
    shell.send('conf t\n')
    shell.send('ip ssh time-out 10\n')
    shell.send('end\n')
    shell.send('show running-config | inc ssh\n')
    time.sleep(2)

    output = shell.recv(10000).decode()
    print(output)
