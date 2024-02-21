-- comando de gunicorn para deployear 
    -- gunicorn -w 4 --reload -b localhost:5000 "app:app"

-- para hacer el requeriments 
pip freeze > requeriments.txt
pip pinstall -r requeriments.txt 


-- venv 
    python -m venv venv
    source ./venv/bin/activate

-- Hacer balanceador 

upstream balanceador{
    server ip1;
    server ip2;
    server ip3;
}

server {
    listen 80;
    location / {
        proxy_pass http://balanceador
    }
}
