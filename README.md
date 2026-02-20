services:
  - type: web
    name: sec-monitor-web
    env: python
    plan: starter
    buildCommand: pip install -r requirements.txt
    startCommand: gunicorn run:app --workers 1 --threads 4 --timeout 120
    disk:
      name: sec-monitor-data
      mountPath: /var/data
      sizeGB: 1
    envVars:
      - key: DATABASE_URL
        value: sqlite:////var/data/sec_tracker.db
      - key: MONITOR_DB_PATH
        value: /var/data/sec_monitor.db
      - key: WATCHLIST_PATH
        value: /var/data/watchlist.json
      - key: MONITOR_SETTINGS_PATH
        value: /var/data/monitor_settings.json
      - key: SEC_USER_AGENT
        sync: false
