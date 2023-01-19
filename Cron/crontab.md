**Home**
- [Home](../index.md)
---

# Crontab

To create a cron entry, you will need to specify the schedule for when the command should be executed, as well as the command itself. The schedule is specified using the following six fields:

- Minute: Specifies the minute of the hour (0-59) when the command should be executed.
- Hour: Specifies the hour of the day (0-23) when the command should be executed.
- Day of the month: Specifies the day of the month (1-31) when the command should be executed.
- Month: Specifies the month of the year (1-12) when the command should be executed.
- Day of the week: Specifies the day of the week (0-6, with 0 being Sunday) when the command should be executed.
- Command: The command or script to be executed.

Each field can contain a single value, a range of values (e.g. 0-5 for the day of the week field), or a list of values separated by commas. An asterisk (*) can be used to match any value in a field.

## Here are some examples of cron entries:

- To execute a command every hour on the hour: 0 * * * * /path/to/command
- To execute a command at 5am every day: 0 5 * * * /path/to/command
- To execute a command at 5am on the first day of the month: 0 5 1 * * /path/to/command
- To execute a command at 5am on the first Monday of the month: 0 5 * * 1 /path/to/command
- To create a cron entry, you can either edit the crontab file for the user you want to run the command as, or create a new crontab file. To edit the crontab file for the current user, you can run crontab -e and add the entry to the file. To create a new crontab file for a different user, you can run crontab -u username -e and specify the username of the user you want to create the crontab file for.

It is a good idea to test your cron entries before scheduling them to ensure that they are working as expected. You can use the crontab -l command to list the tasks in a user's crontab file, and the crontab -r command to remove all tasks from a user's crontab file.

Please note that cron entries are sensitive to whitespace, so be sure to separate the fields with a single space or tab character. It is also a good idea to include a newline character at the end of the entry to ensure that it is correctly interpreted by cron.
