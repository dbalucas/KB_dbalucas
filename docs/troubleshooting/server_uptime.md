# Display server uptime with SQL

Issue following SQL command to show the database system uptime:
`SELECT date_trunc('second', current_timestamp - pg_postmaster_start_time()) as uptime;`
