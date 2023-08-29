"# ip_derper"
下载
git clone git remote add origin https://github.com/alanmoleapfive/ip_derper.git
cd ip_derper
构建
docker build -t leapfive/ip_derper:v1.48.1 .
运行
docker run --restart always \
--name derper -p 10443:12345 -p 10480:12346 -p 3478:3478/udp \
-v /var/run/tailscale/tailscaled.sock:/var/run/tailscale/tailscaled.sock \
-e DERP_CERT_MODE=manual \
-e DERP_ADDR=:12345 \
-e DERP_HTTP_PORT=12346 \
-e DERP_VERIFY_CLIENTS=true \
-d leapfive/ip_derper:v1.48.1
