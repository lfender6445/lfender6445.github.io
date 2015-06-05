---
layout: post
title: "RabbitMQ server error"
description: ""
category:
tags: []
---

RabbitMQ server error


UPDATED error message

I am getting a BOOT FAILED error every time I try to start the rabbitmq server. Does anybody know how I can fix this? I have attached the error message. I have tried a few different things including uninstalling and reinstalling it and am now getting a new error message, but am at a loss for what to try next. Any suggestions are much appreciated! Thank you!!

    BOOT FAILED
    ===========
    
    
    Error description:
{error,
    {schema_integrity_check_failed,
        [{table_missing,rabbit_exchange_serial},
         {table_missing,rabbit_runtime_parameters},
         {table_missing,rabbit_durable_queue},
         {table_missing,rabbit_queue},
         {table_missing,gm_group},
         {table_missing,mirrored_sup_childspec}]}}
    
    
    Log files (may contain more information):
/usr/local/var/log/rabbitmq/rabbit@localhost.log
/usr/local/var/log/rabbitmq/rabbit@localhost-sasl.log
    
    
    Stack trace:
[{rabbit_mnesia,ensure_schema_integrity,0,
                [{file,"src/rabbit_mnesia.erl"},{line,519}]},
 {rabbit_mnesia,init_db,3,[{file,"src/rabbit_mnesia.erl"},{line,450}]},
 {rabbit_mnesia,init_db_and_upgrade,3,
                [{file,"src/rabbit_mnesia.erl"},{line,458}]},
 {rabbit_mnesia,init,0,[{file,"src/rabbit_mnesia.erl"},{line,99}]},
 {rabbit,'-run_boot_step/1-lc$^1/1-1-',1,
         [{file,"src/rabbit.erl"},{line,488}]},
 {rabbit,run_boot_step,1,[{file,"src/rabbit.erl"},{line,487}]},
 {rabbit,'-start/2-lc$^0/1-0-',1,[{file,"src/rabbit.erl"},{line,453}]},
 {rabbit,start,2,[{file,"src/rabbit.erl"},{line,453}]}]
    
    
    
    
    
    
    BOOT FAILED
    ===========
    
    
    Error description:
{could_not_start,rabbit,
    {bad_return,
        {{rabbit,start,[normal,[]]},
         {'EXIT',
             {rabbit,failure_during_boot,
                 {error,
                     {schema_integrity_check_failed,
                         [{table_missing,rabbit_exchange_serial},
                          {table_missing,rabbit_runtime_parameters},
                          {table_missing,rabbit_durable_queue},
                          {table_missing,rabbit_queue},
                          {table_missing,gm_group},
                          {table_missing,mirrored_sup_childspec}]}}}}}}}
    
    
    Log files (may contain more information):
/usr/local/var/log/rabbitmq/rabbit@localhost.log
/usr/local/var/log/rabbitmq/rabbit@localhost-sasl.log
    
    
    {"init terminating in do_boot",{rabbit,failure_during_boot,{could_not_start,rabbit,{bad_return,{{rabbit,start,[normal,[]]},{'EXIT',{rabbit,failure_during_boot,{error,{schema_integrity_check_failed,[{table_missing,rabbit_exchange_serial},{table_missing,rabbit_runtime_parameters},{table_missing,rabbit_durable_queue},{table_missing,rabbit_queue},{table_missing,gm_group},{table_missing,mirrored_sup_childspec}]}}}}}}}}}
    
    
    Crash dump was written to: erl_crash.dump
    init terminating in do_boot ()


--------------------------------------- 
This occurred for me during a rabbitmq upgrade with brew.

It was easier for me to just remove the directory all together and install from scratch.

    sudo rm -rf /usr/local/var/rabbitmq/
    brew uninstall rabbitmq; 
    brew install rabbitmq
    rabbitmq-server


