FROM n8nio/base:20

# Instala dependencias básicas (útil para debugging, aunque no esencial para producción)
RUN apk add --no-cache --update openssh sudo shadow bash

# Permite a node usar sudo (no suele ser necesario para producción)
RUN echo node ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/node && chmod 0440 /etc/sudoers.d/node

# Crea y otorga permisos a /workspaces
RUN mkdir /workspaces && chown node:node /workspaces

# Cambia al usuario node
USER node

# Prepara el almacenamiento de pnpm (si estás usando pnpm en tu proyecto)
RUN mkdir -p ~/.pnpm-store && pnpm config set store-dir ~/.pnpm-store --global

# Expone el puerto para n8n
EXPOSE 5678

# Comando por defecto para arrancar n8n
CMD ["n8n", "start"]
