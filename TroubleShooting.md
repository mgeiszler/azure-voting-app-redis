# NOTE: docker-compose file does NOT support "imagePullPolicy" and "imagePullSecrets", so image gets built unless the image was already pulled or built.
  azure-vote-front:
    build: ./azure-vote
    image: mycontainerregistryjenkinskub.azurecr.io/azure-vote-front:kube4
    imagePullPolicy: IfNotPresent
    container_name: azure-vote-front
    environment:
      REDIS: azure-vote-back
    ports:
        - "8080:80"
    imagePullSecrets:
      - name: acr-secret1mg
