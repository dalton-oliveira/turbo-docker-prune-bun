FROM oven/bun:1 AS base

FROM base AS builder
WORKDIR /usr/src/app

RUN bun add --global turbo
COPY . .
RUN turbo prune @pkg/a --docker

FROM base AS installer
RUN bun add --global turbo

WORKDIR /usr/src/app
COPY --from=builder /usr/src/app/out/json/ .
RUN bun install --production
