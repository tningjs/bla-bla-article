# Making An Audio Based Social App

Author: Tao Ning
Source Code:

- [metal-bat-web](https://github.com/taoning2014/metal-bat-web)
- [metal-bat-api](https://github.com/taoning2014/metal-bat-api)

Index

1. Introduce app functionality
    1. Why
    2. What
2. The UI and routes
3. The tech stack and architecture (including Heroku, Github)
4. Leancloud and the login service, how to create rooms
5. Leancloud live query
6. Agora SDK
7. Genos service
8. Agora service
9. Invitation code
10. Intel

## Part I - Introduce app functionality

### Why

In the mid of may this year, our Team hosted a three day hackathon which gives us freedom to create whatever we want. I was impressed by the simplicity of an audio based app Clubhouse, and feel degression due to I doesn't have an invitation code and it is iOS only to try it out when it becomes popular eariler this year. So, I think it will be fantastic if I could create a similar web app that everyone can access with a Morden browser.

In the following articles I will talk about how I create this app with my mentor and good budy Sean.

### What

With that being said, I'd like you to try it out first. 

> notice: you may need to invite a friend to the chat room to try the audio feature, if you don't want to talk to yourself ;)

We get our custom domain and deploy the app to Heroku with SSL enabled, so you can visit it at: https://bla-bla.app

Like the reguar app, the first thing you need to do it register an user account, you can select an avatar that resmebles yourself or your pets (Credits: thanks to Lora who helped to draw these funny pixed images). Ah, right, please remember you do need an invitation code, we will show you how to generate random ones through the code later, for now, you can use a generatic one `RTE2021`. The email address is not required, but if you want to create a chat room yourself, we do need you to gives us an valid email address, by which we means we will send you email to verify, again, we will show you how we did that in the code later.

<!-- Todo: Image of the register route -->

After login, it will route you to the home page where it shows the current room, scheduled room and recorded room. We get 2 ~ 3 rooms created weekly, so likely you won't see any room you can join. But we do have some recorded content that our host Michael has created in the past. If you click the first link, it will route you to a separate website with a similar address https://bla-bla.club. I designed and made this Wordpress website to my friends who like to host talk shows on bla-bla as a bonus.

<!-- Todo: Add TWM -->

It will be more fun if you can create your own room and invite friends to join and talk. So, let's do it. Try to click the button on the top left "Create a room", oops, if you see the following errors, which means you do not have the permisssion to create a room yet. What should you do? 

Yes! Like I said before, you need to verifiy your email address. Let's hover your mouse over your avatar on the top right corner, and click the setting dropdown, after following the instructions there, you will get an email notification to verifiy your email address. After that, click the "Create a room" again, it will gareenti works now, and you should see the following room page. You can pretty much do any thing you like: talk, send message, click reaction (by hovering mouse over the heart on the bottom right), if host others so that they can talk too. If there is someone else join the room, they can hear you talk, see those actions in real time thanks to the backend services Agoar and Leanclould. We kept on getting feedbacks that the sounds quality is great when Michael host his talk show and audience joined globally.

<!-- Todo: TWM room link -->

Well, that's enough for the introduction. Try it out, and gives us feedback (or even better, improve it by sending us your PR).

### How

This is just an overview, if you try it out, you will find more features. Now, let's jump right into the tech details.