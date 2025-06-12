FROM node:18-alpine

RUN npm install -g pnpm

WORKDIR /app

COPY pnpm-lock.yaml pnpm-workspace.yaml package.json ./

# Copy all workspace packages
COPY apps/backend ./apps/backend
COPY packages/database ./packages/database
# Add other workspace packages if needed

RUN pnpm install --frozen-lockfile

# Build backend using pnpm filter (runs tsc inside backend with deps available)
RUN pnpm --filter @meridian/backend run build

EXPOSE 8000

CMD ["pnpm", "--filter", "@meridian/backend", "start"]
