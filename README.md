  GNU nano 6.2                                         /etc/nginx/sites-enabled/default *                                                
    location /media/ {
        alias /var/www/kittygram/media/
    }



    location / {
        root   /var/www/kittygram;
        index  index.html index.htm;
        try_files $uri /index.html;
    }


    listen 443 ssl; # managed by Certbot
    ssl_certificate /etc/letsencrypt/live/kittygramtestanton.zapto.org/fullchain.pem; # managed by Certbot
    ssl_certificate_key /etc/letsencrypt/live/kittygramtestanton.zapto.org/privkey.pem; # managed by Certbot
    include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot

}




 server {
    if ($host = kittygramtestanton.zapto.org) {
        return 301 https://$host$request_uri;
    } # managed by Certbot



    listen 80;
    server_name kittygramtestanton.zapto.org;
    return 404; # managed by Certbot


}


