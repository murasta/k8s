https://docs.docker.com/compose/compose-file/05-services/



services:
  redis:
    image: redis
    volumes:
      - db_data:/data
  python:
    image: krajewskim/python-api:new
    depends_on:
      - redis
    environment:
      - REDIS_HOST=redis
    ports:
      - 5002:5002
volumes:
  db_data:



  https://github.com/hadolint/hadolint

  docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest

  docker system prune -a --volumes


  ===============================
  ~/.kube/config

  https://kubernetes.io/docs/tasks/tools/install-kubectl-windows/#enable-shell-autocompletion

  https://kubernetes.io/docs/tasks/tools/install-kubectl-macos/#enable-shell-autocompletion


  krajewskim/python-api:new

  