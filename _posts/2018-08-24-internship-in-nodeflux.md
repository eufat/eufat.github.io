---
title: "Nodeflux Software Engineering Internship"
---

## Background

On the sixth to seventh semester break, I was obliged to take a practical work. Generally, friends in instrumentation physics minor take practical work at LIPI, BPPT, BATAN, and other state research institutions. However, I would like to seek experience in a technology company that deals with computer vision. Why computer vision? because, later my thesis will be directed at this topic and one of my projects that has been funded by DIIB UI and RISTEKDIKTI is also deal with computer vision. So, if the thesis, internship and project can go one way, why not?

## Rejected

Initially I applied for internships to several companies in Malaysia and Singapore because I wanted to try to work outside Indonesia and as well as be able to save money, I have tried to Intel in Penang Malaysia, [Visenze](https://www.visenze.com/) in Singapore and [nuTonomy](https://www.nutonomy.com/) also in Singapore. But unfortunately, at Intel I was rejected (maybe because of I am Indonesian), Visenze was resigned from his internship and nuTonomy had no news. It's sad, hahaha.

## Got Nodeflux!

However, it turns out that after a long web browsing, there is one startup in Indonesia that focuses on computer vision, the name of the startup is [Nodeflux](https://nodeflux.io/). Nodeflux is a startup that has a product in the form of IVA (Intelligent Video Analytics), so with Nodeflux we can analyze content on video with a CCTV camera as an instrument. Uniquely, Nodeflux is the only company in Indonesia that is involved in IVA, there is no competitor at the time. Nodeflux is also the only startup in Indonesia to participate in the [NVIDIA Inception](https://www.nvidia.com/en-us/deep-learning-ai/startups/) accelerator. NVIDIA Inception is an accelerator that supports startups with artificial intelligence (AI) and deep learning technology. If you look at the Nodeflux website [here](https://nodeflux.io/), the clients are the big ones, one of their clients is BIN (National Intelligence Agency), is that really cool? similar to the Bourne movies.

## Passing the TA

After applying at Nodeflux, I was given a technical assignment (TA), there were 14 questions. But, I can only solve 10 questions, the solution I submitted is [here](https://github.com/eufat/nodeflux-ta). The TA is relatively easy but the topic is very broad, I can do all web questions because I have enough experience and have been internships and do a lot of web development before. Actually, what is being demanded is not a lot of problems to be done, because what is being assessed is the approach of the solution. Not long after passing the TA, there was an online interview. After waiting for a while I finally passed and was accepted by the internship there, hooray.

## The Office

The Nodeflux office is at Kemang, the office is actually a large house, not office, there is a swimming pool there. Internship there, the clothes are casual so it's not complicated, I really like it like this. There is a kitchen too, so you can cook, we are often given food and snacks for free hahaha. Because the location is at Kemang, it is relatively far from the UI campus, about 1 hour to go there with a combination of bikun, train and grab. Usually, I was the than the other guys hahaha, because I left at 9.30, got there at 10.30. There is a reason why I'm late, because when I go at 8:00 by train, the train looks like a sacrificial goat truck, tight, hot and smelly. The point when you arrive at the office you will not in the mood anymore.

## The Work

During the internship I and other intern friends (from UI, ITS and ITB) made various projects. At the beginning of the internship, we created a system for benchmarking message brokers such as RabbitMQ, Redis, NSQ and Apache Kafka for transmitting image frames to video. Here I am tasked with processing and visualizing data with the [ELK stack](https://www.elastic.co/elk-stack) stack (Elasticsearch, Logstash and Kibana) for later analysis, which system is the most resource efficient, fast and reliable. In this task, the most challenging is the Logstash configuration which is useful for filtering and processing data before being accepted by Elasticsearch.

In the middle of the internship we combined a message broker, object detector, and streamer to measure system performance end-to-end, here I was tasked with creating an object detector with the CNN model and creating a simple image streaming system using WebSocket. I also learn several deep learning model architectures for real-time object detection such as [MobileNet](https://arxiv.org/abs/1704.04861) and [YOLO](https://arxiv.org/abs/1506.02640).

At the end of my internship, my job was to try various streaming methods using different transmission protocols such as RTP / RTSP, DASH and WebRTC. Of these three protocols, the most difficult to implement is WebRTC, because Nodeflux needs streaming server-to-client direction, which is different from the general communication used by WebRTC, namely realtime client-to-client communication. Besides that, the lack of a mature library and examples is a problem in itself. In between the three main projects, I also took the time to create two simple internal tools, namely the React application and the Python CLI to help engineers at Nodeflux in validating and conducting data gatherings.

## Perks & Moments

There are perks and unique moments during the internship. Perks, for experimentation only, some virtual machines are rented out specifically for interns, one of these virtual machines is powered by [NVIDIA Tesla V100] (https://www.nvidia.com/en-us/data-center/tesla-v100/) GPU for datacenter with the highest performance to date, the calculation speed is up to 120 TFLOPS (120 trillion operations per second). The unique moment, during the internship, Nodeflux was being covered by MetroTV, so it was funny that when we programming beside the camera man taking pictures, it is so awkward, Hahaha. When indepence day celebration, we had competitions at Nodeflux, lots of prizes and then finally the swimming pool at Nodeflux was used hahaha. But unfortunately, I didn't come because I had work to do on campus, even so I still got one of the doorprizes, Miniso's umbrella, yeah.

Overall, internships at Nodeflux are cool and challenging but still fun and the people are chill.

The results of this internship presentation are [here](/docs/presentation-kp.pdf)
