cd "/Users/brett.schroeder/Documents/New project"
git checkout main
git add render.yaml Procfile requirements.txt app/__init__.py app/monitor_service.py app/routes.py templates/monitor.html README.md
git commit -m "Add Render blueprint and hosted monitor config"
git push origin main
