## About
Guide on how to:
- Enable log rotation either by size or date
- Enable runtime rendering, i.e. human readable date and time in logs instead of UNIX timestamp

## Log rotation by size

![image](https://github.com/user-attachments/assets/eb40d145-e9ca-4f1a-af28-172da813836c)

1. `nsradmin -p nsrexec`
2.	`. type: NSR log; name: <log.raw>` #Replace '<log.raw>' with the name of the log you want to enable rotation on
3.	`print`
4.	`update runtime rollover by size “Enabled”`
5.	`y`

When the defined threshold value is reached, NetWorker truncates the current log to 0 MB and creates a new file with the name convention `log_date_time.raw`

![image](https://github.com/user-attachments/assets/cd5f645a-2aef-483f-85c0-5302ad729a19)

## Log rotation by date

Same process as in ## Log rotation by size simply replace **step 4** with one of the following values:

- Daily rotation by time: `update runtime rollover by time: "00:00"`
- Weekly rotation by weekday: `update runtime rollover by time: "sunday"`
- Monthly rotation by a given day of the month: `update runtime rollover by time: "15 day every month"`

## Enable runtime rendering

- By default, runtime rendering is disabled, in order to enable it, you must specify a path and a new log name
- The rendered and unrendered logs are written simultaneously

1.	`nsradmin -p nsrexec`
2.	`. type: NSR log; name: daemon.raw`
3.	`print`
4.	`update runtime rendered log: /nsr/logs/log_name.log`
5.	`y`

![image](https://github.com/user-attachments/assets/e1ab24d5-1b5d-4e0f-8939-8967e68a9a53)

![image](https://github.com/user-attachments/assets/1b88bcc0-3458-4c41-8b29-8ad5c2a7c337)


