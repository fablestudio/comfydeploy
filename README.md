# ComfyDeploy

Re: Open-sourcing ComfyDeploy

TL;DR: We are open-sourcing ComfyDeploy again, with full platform backend + frontend.

[Discord](https://discord.gg/qtHUaVNRVM) | [Website](https://www.comfydeploy.com)

---

### How we got here?

In late 2023, I started ComfyDeploy as an open source project while I was working at my previous company. We had a problem deploying ComfyUI to our production server due to how complicated it is to get ComfyUI into a serverless environment.

Little did I know I was going to meet my co-founder Nick and embark on a journey I never dreamt of.

I posted on Twitter about this little project that I was working on as an indie hacker, and it blew up overnight. I woke up to 100k impressions on the post. I put up my cal link and people started scheduling calls. I got to talk to a bunch of people across the globe, with people reaching out to help or potentially use ComfyDeploy.

Nick was one of the early contributors, and later we decided to apply to a bunch of accelerators together. It was early February, just a couple of weeks after we met. We applied to YC—we were unsure if we would even get in, but we still decided to quit our jobs, and the day after we quit, we got in.

It was insane to even think that we would have had a chance.

### Life Changing Decision

We immediately said yes.

We got into YC with ComfyDeploy around 2.5K MRR.

Around the same timeframe, ComfyOrg was introduced, Stability collapsed, and Flux just came out.

We kept building ComfyDeploy, for months, and kept things going.

The company was growing, but very slowly. We realized the biggest issue is that we are still really early, and it takes time for businesses and enterprises to really adopt such a niche tool. And we are not ComfyOrg.

### Dynamic Changes

Meanwhile, closed source models dropped, and a bunch of workflows that we knew became no longer useful.

Coming from a game developer background, I saw huge potential with ComfyUI at first, but I never would have imagined that one giant model could do exactly what you put into words, and you still need workflows to fine-tune and control the exact outputs. And ComfyDeploy did make it possible for teams to experiment with this.

We were just unsure about the future of the company. While we kept getting more and more business inquiries about ComfyUI, this is what really kept us going before giving up. It's a mixed signal.

Meanwhile, my friends bootstrapped their mobile app to $500k a month. I was really stressed—were we going to live up to the aspirations that we set out, both personally and for the company?

### Problems

I feel immensely grateful for the customers that we were able to help, and this is something I feel forever privileged to experience—working with the best creative teams across the globe and brands that I look up to.

But we were stuck in the middle. First, we are not ComfyOrg; second, closed source models were doing things way better and slowly eating up the market.

And it's inevitable that ComfyOrg will have some sort of cloud solution. And we do appreciate all the work ComfyOrg has put into making ComfyUI great again. We realized we would be competing in some ways especially in the cloud space, and we could never grow out of this, which constrained the company's growth at the same time.

As of today, ComfyDeploy is doing $29k MRR, and our last 30 days' revenue was $50k processed. Which is the highest we have ever got, but also the most depressing day I have ever had.

### So what now?

We have been working for months on our pay-as-you-go tier—no longer requiring you to talk to us, just pay for the cloud resources you use. And also, going back to our roots: open-sourcing the ENTIRE CLOUD PLATFORM while continuing to support existing customers.

Our current customers and creative teams are the people who kept us going for the last year, and I will be forever grateful. But this might just not be the field for us, and we respect Comfy and do not want to get in the way. And I think it's going to be really good for everyone.

#### What does this mean for current customers: 

The service will stay online and supported until the last standing user!

#### What does this mean for future customers: 
You can either go with the pay-as-you-go tier to get started, or self-host the entire platform. If ComfyOrg eventually builds something like ComfyDeploy, the official solution will be recommended by us!

#### What does this mean for ComfyDeploy team: 

We will continue supporting existing customers. At the same time we will start exploring new ideas. And this does not mean the end to us. But rather a fresh start. Stay tuned for what's coming next.

#### What I will be doing for the next couple days
1. Documentation and tutorials to set up ComfyDeploy
2. Explore new problems that could resonate with us.

### Credits

A list of credits that got us here (doesn't go in order)
Comfy, Nick, Karrix, Jeff, Edgar, Ecjojo, Brad, Aashay and Semil, Jon, Choco, Modal, Vercel, Triton, Emmanuel, Julien, and many more.

---

Follow our journey on Twitter [@bennykokmusic](https://x.com/bennykokmusic)


## Local Setup

Make sure you have docker (orbstack), bun, and uv installed.

```
bun i
```

```
bun run dev
```

Copy env example

```
cp apps/app/.env.example apps/app/.env
cp apps/api/.env.example apps/api/.env
```

### API


### S3
```
# S3 <Better use a hosted version for dev>
SPACES_BUCKET_V2=
SPACES_ENDPOINT_V2=
SPACES_REGION_V2=
SPACES_KEY_V2=
SPACES_SECRET_V2=
```

### NGROK This is for tunneling, free account will do
```
NGROK_AUTHTOKEN=
NGROK_DOMAIN=
```

### Setup a clerk account for auth, free acount will do
```
CLERK_PUBLIC_JWT_KEY=
CLERK_SECRET_KEY=
```

### JWT Secret for API and secret
```
# generate using -> openssl rand -hex 32
JWT_SECRET="test-secret-key"
# python3 -c "from cryptography.fernet import Fernet; print(Fernet.generate_key().decode('utf-8'))"
SECRET_ENCRYPTION_KEY=
```

```
GITHUB_TOKEN=github_pat_
```

You can actually use the same Redis server for all
```
UPSTASH_REDIS_META_REST_URL="http://localhost:8079"
UPSTASH_REDIS_META_REST_TOKEN="example_token"

UPSTASH_REDIS_REST_URL_LOG="http://localhost:8079"
UPSTASH_REDIS_REST_TOKEN_LOG="example_token"

UPSTASH_REDIS_REST_URL_REALTIME="http://localhost:8079"
UPSTASH_REDIS_REST_TOKEN_REALTIME="example_token"

REDIS_URL_LOG=redis://localhost:6379/0
REDIS_URL_REALTIME=redis://localhost:6379/0
```

### CURRENT_API_URL
Point to your ngrok url for local dev
```
CURRENT_API_URL="https://"
```

### Modal Env, setup a modal account, free account will do

MODAL_ENVIRONMENT="main"
MODAL_TOKEN_ID=""
MODAL_TOKEN_SECRET=""


## App

```
NEXT_PUBLIC_CD_API_URL=http://localhost:3011
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=
NEXT_PUBLIC_NGROK_CD_API_URL=https://
```

### Cloud Component

```
Modal
Neon for db
Vercel for frontend -> App repo
Backend for railway / any serverless / stateful server
Clerk for auth
Upstash for redis
AWS S3 for storage
```