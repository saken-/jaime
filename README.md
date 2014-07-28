jaime
=====

Serves as a service manager for some service/plugins, spawns them let the user talk to them (through a plugin), keeps them online and reboot/log/alert accordingly.

Basic scheme:

jaime will be runningas a daemon (jaimed)

jaime will have plugin config files, which will be JSON files stating a binary to run, and any parameters it could need.

messages from the plugin to jaime will be JSON files stating who the message is meant for and any other fields relevant to that service.

JSON structures as follows:

Config files

{"service":"binary_name",
 "params":[
            {"arg_1":"val_1"},
            {"arg_2":"val_2"},
            .....
            {"arg_n":"val_n"}
            ]
}

Message JSON

Note: jaime service name is jaime

{"dest_service":"service_name"
 "message":[
            {"arg_1":"val_1"},
            {"arg_2":"val_2"},
            .....
            {"arg_n":"val_n"}
            ]
}


All services must accept the following messages:

service:name,
action:ONLINE/OFFLINE/SHUTDOWN/STATUS
 

Reply with

service:jaime
result:ONLINE/OFFLINE (for action:STATUS)
result:OK/ERROR       (for ONLINE/OFFLINE/SHUTDOWN)



