<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Liskun — Custom Birthday Websites</title>

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@400;500;600;700&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">

<style>

:root{
    --black:#030303;
    --black2:#080607;
    --burgundy:#210b10;
    --burgundy2:#3a1119;
    --gold:#d7b36a;
    --gold2:#f0d99b;
    --cream:#eee4d0;
    --text:#c1b8aa;
    --muted:#766e64;
    --line:rgba(215,179,106,.20);
}

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

html{
    scroll-behavior:smooth;
}

body{
    background:
        radial-gradient(circle at 50% -10%,rgba(94,24,39,.35),transparent 35%),
        linear-gradient(180deg,#030303,#080607 45%,#030303);
    color:var(--text);
    font-family:"DM Sans",sans-serif;
    overflow-x:hidden;
}

/* =========================================
   CINEMATIC GRAIN
========================================= */

body::before{
    content:"";
    position:fixed;
    inset:0;
    pointer-events:none;
    z-index:9999;
    opacity:.035;

    background-image:url(
        "data:image/svg+xml,%3Csvg viewBox='0 0 180 180' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='.5'/%3E%3C/svg%3E"
    );
}

/* =========================================
   FLOATING STARS
========================================= */

#stars{
    position:fixed;
    inset:0;
    pointer-events:none;
    overflow:hidden;
    z-index:1;
}

.star{
    position:absolute;
    border-radius:50%;
    background:#f4dfac;

    box-shadow:
        0 0 5px rgba(240,217,155,.8),
        0 0 12px rgba(215,179,106,.35);

    animation:
        floatStar linear infinite,
        twinkle ease-in-out infinite alternate;
}

@keyframes floatStar{

    from{
        transform:translate3d(0,110vh,0);
    }

    to{
        transform:translate3d(var(--drift),-15vh,0);
    }
}

@keyframes twinkle{

    from{
        opacity:.15;
        transform:scale(.7);
    }

    to{
        opacity:.9;
        transform:scale(1.35);
    }
}

/* =========================================
   MUSIC
========================================= */

.music-bar{
    position:relative;
    z-index:20;
    width:100%;
    padding:14px 20px;

    background:rgba(3,3,3,.94);

    border-bottom:1px solid var(--line);

    backdrop-filter:blur(18px);

    text-align:center;
}

.music-label{
    font-size:10px;
    letter-spacing:4px;
    color:var(--muted);
    margin-bottom:7px;
}

audio{
    width:min(500px,92%);
    height:34px;
}

/* =========================================
   COMMON
========================================= */

section{
    position:relative;
    z-index:2;
    padding:110px 7%;
}

.container{
    max-width:1150px;
    margin:auto;
}

.eyebrow{
    font-size:10px;
    letter-spacing:5px;
    color:var(--gold);
    text-transform:uppercase;
    margin-bottom:18px;
}

h1,h2,h3{
    font-family:"Cormorant Garamond",serif;
    color:var(--cream);
    font-weight:500;
}

h2{
    font-size:clamp(45px,7vw,82px);
    line-height:.92;
}

p{
    line-height:1.8;
}

.gold{
    color:var(--gold2);
}

.center{
    text-align:center;
}

/* =========================================
   BUTTON
========================================= */

.btn{
    display:inline-flex;
    align-items:center;
    justify-content:center;

    min-height:50px;
    padding:0 27px;

    border:1px solid rgba(215,179,106,.6);

    color:var(--gold2);
    text-decoration:none;

    font-size:11px;
    letter-spacing:2px;
    text-transform:uppercase;

    transition:.35s ease;

    background:rgba(215,179,106,.03);
}

.btn:hover{
    background:var(--gold);
    color:#080604;

    box-shadow:
        0 0 35px rgba(215,179,106,.18);

    transform:translateY(-2px);
}

/* =========================================
   HERO
========================================= */

.hero{
    min-height:92vh;

    display:flex;
    align-items:center;
    justify-content:center;

    text-align:center;

    overflow:hidden;
}

.hero::before{
    content:"";

    position:absolute;

    width:650px;
    height:650px;

    border-radius:50%;

    background:
        radial-gradient(
            circle,
            rgba(91,20,36,.30),
            transparent 70%
        );

    filter:blur(15px);
}

.hero-content{
    position:relative;
    max-width:950px;
}

.brand{
    font-size:12px;
    letter-spacing:8px;
    color:var(--gold);
    margin-bottom:32px;
}

.hero h1{
    font-size:clamp(58px,10vw,130px);
    line-height:.78;
    margin-bottom:35px;
}

.hero h1 span{
    display:block;
    color:var(--gold2);
}

.hero-text{
    max-width:650px;
    margin:0 auto 40px;

    color:#a79d90;

    font-size:15px;
}

.hero-buttons{
    display:flex;
    gap:14px;
    justify-content:center;
    flex-wrap:wrap;
}

.scroll{
    position:absolute;
    bottom:25px;
    left:50%;

    transform:translateX(-50%);

    font-size:9px;
    letter-spacing:4px;

    color:#625b52;
}

/* =========================================
   EXPERIENCE
========================================= */

.experience{
    background:
        linear-gradient(
            180deg,
            transparent,
            rgba(33,11,16,.45),
            transparent
        );
}

.demo-box{
    max-width:900px;

    margin:55px auto 0;

    border:1px solid var(--line);

    background:rgba(10,8,8,.75);

    padding:55px;

    position:relative;

    overflow:hidden;
}

.demo-box::after{
    content:"";

    position:absolute;

    width:300px;
    height:300px;

    right:-120px;
    top:-120px;

    background:
        radial-gradient(
            circle,
            rgba(215,179,106,.13),
            transparent 70%
        );
}

.demo-top{
    display:flex;
    justify-content:space-between;

    border-bottom:1px solid var(--line);

    padding-bottom:18px;
    margin-bottom:40px;
}

.demo-top span{
    font-size:9px;
    letter-spacing:3px;
    color:var(--muted);
}

.demo-title{
    font-family:"Cormorant Garamond",serif;

    font-size:58px;

    color:var(--cream);

    line-height:.95;

    margin-bottom:20px;
}

.demo-message{
    max-width:550px;

    color:#aaa093;

    margin-bottom:35px;
}

.countdown{
    display:flex;
    gap:30px;

    flex-wrap:wrap;

    margin-bottom:35px;
}

.time{
    text-align:center;
}

.time strong{
    display:block;

    font-family:"Cormorant Garamond",serif;

    font-size:42px;

    color:var(--gold2);
}

.time small{
    font-size:8px;

    letter-spacing:3px;

    color:var(--muted);
}

/* =========================================
   ATTENTION
========================================= */

.problem{
    text-align:center;
}

.problem h2{
    max-width:900px;
    margin:auto;
}

.problem p{
    max-width:650px;

    margin:30px auto;

    color:#9d9386;
}

/* =========================================
   OFFER
========================================= */

.offer{
    padding-top:130px;
    padding-bottom:130px;
}

.offer-box{
    position:relative;

    max-width:1050px;

    margin:auto;

    padding:80px 60px;

    text-align:center;

    background:
        radial-gradient(
            circle at 50% 0%,
            rgba(114,29,47,.45),
            transparent 50%
        ),
        linear-gradient(
            135deg,
            #120709,
            #090606
        );

    border:1px solid rgba(215,179,106,.3);

    box-shadow:
        0 0 80px rgba(45,10,18,.35),
        inset 0 0 80px rgba(215,179,106,.025);
}

.offer-box h2{
    font-size:clamp(48px,7vw,85px);
    margin-bottom:25px;
}

.price{
    font-family:"Cormorant Garamond",serif;

    font-size:80px;

    color:var(--gold2);

    line-height:1;

    margin:25px 0;
}

.price small{
    font-family:"DM Sans",sans-serif;

    font-size:12px;

    letter-spacing:4px;

    color:var(--muted);
}

.offer-description{
    max-width:650px;

    margin:0 auto 35px;

    color:#aaa093;
}

/* =========================================
   TYPES
========================================= */

.types-grid{
    display:grid;

    grid-template-columns:repeat(5,1fr);

    gap:12px;

    margin-top:55px;
}

.type{
    min-height:150px;

    border:1px solid var(--line);

    display:flex;

    flex-direction:column;

    align-items:center;
    justify-content:center;

    text-align:center;

    padding:20px;

    background:rgba(255,255,255,.012);

    transition:.4s ease;
}

.type:hover{
    border-color:rgba(215,179,106,.6);

    transform:translateY(-5px);

    background:rgba(215,179,106,.025);
}

.type-number{
    font-family:"Cormorant Garamond",serif;

    color:var(--gold);

    font-size:30px;

    margin-bottom:10px;
}

.type-name{
    font-size:10px;

    letter-spacing:3px;

    text-transform:uppercase;

    color:#bdb3a6;
}

/* =========================================
   FEATURES
========================================= */

.features{
    background:
        linear-gradient(
            180deg,
            transparent,
            rgba(28,8,13,.4),
            transparent
        );
}

.features-grid{
    display:grid;

    grid-template-columns:repeat(4,1fr);

    gap:15px;

    margin-top:65px;
}

.feature{
    min-height:190px;

    padding:28px;

    border:1px solid var(--line);

    background:rgba(5,5,5,.5);

    transition:.4s;
}

.feature:hover{
    transform:translateY(-6px);

    border-color:
        rgba(215,179,106,.55);
}

.feature-number{
    font-family:"Cormorant Garamond",serif;

    color:var(--gold);

    font-size:28px;

    margin-bottom:25px;
}

.feature h3{
    font-size:25px;

    margin-bottom:10px;
}

.feature p{
    font-size:12px;

    color:#81786d;

    line-height:1.6;
}

/* =========================================
   HOW IT WORKS
========================================= */

.steps{
    max-width:900px;

    margin:60px auto 0;
}

.step{
    display:grid;

    grid-template-columns:80px 1fr;

    gap:25px;

    padding:30px 0;

    border-bottom:1px solid var(--line);
}

.step-no{
    font-family:"Cormorant Garamond",serif;

    font-size:48px;

    color:var(--gold);
}

.step h3{
    font-size:30px;

    margin-bottom:5px;
}

.step p{
    font-size:13px;

    color:#81786d;
}

/* =========================================
   MEMORY
========================================= */

.memory{
    text-align:center;
}

.memory-card{
    max-width:800px;

    margin:55px auto 0;

    padding:70px 35px;

    border-top:1px solid var(--line);

    border-bottom:1px solid var(--line);
}

.memory-card h3{
    font-size:clamp(38px,6vw,68px);

    line-height:1;

    margin-bottom:25px;
}

.memory-card p{
    color:#93897c;

    max-width:570px;

    margin:auto;
}

/* =========================================
   CONTACT
========================================= */

.contact{
    text-align:center;

    padding-bottom:80px;
}

.contact h2{
    margin-bottom:25px;
}

.contact-text{
    max-width:600px;

    margin:0 auto 35px;

    color:#978d80;
}

.contact-note{
    margin-top:25px;

    font-size:10px;

    letter-spacing:2px;

    color:#5d564e;
}

/* =========================================
   FOOTER
========================================= */

footer{
    position:relative;

    z-index:2;

    padding:35px 20px;

    border-top:
        1px solid
        rgba(215,179,106,.12);

    text-align:center;
}

footer strong{
    font-family:"Cormorant Garamond",serif;

    color:var(--gold2);

    font-size:23px;
}

footer p{
    margin-top:6px;

    font-size:9px;

    letter-spacing:3px;

    color:#5e574f;

    text-transform:uppercase;
}

/* =========================================
   SCROLL REVEAL
========================================= */

.reveal{
    opacity:0;

    transform:translateY(35px);

    transition:
        1s
        cubic-bezier(.2,.7,.2,1);
}

.reveal.visible{
    opacity:1;

    transform:translateY(0);
}

/* =========================================
   RESPONSIVE
========================================= */

@media(max-width:900px){

    .types-grid{
        grid-template-columns:
            repeat(2,1fr);
    }

    .features-grid{
        grid-template-columns:
            repeat(2,1fr);
    }

    .offer-box{
        padding:60px 25px;
    }
}

@media(max-width:600px){

    section{
        padding:80px 6%;
    }

    .hero{
        min-height:85vh;
    }

    .hero h1{
        font-size:64px;
    }

    .brand{
        font-size:9px;
        letter-spacing:5px;
    }

    .demo-box{
        padding:30px 22px;
    }

    .demo-title{
        font-size:46px;
    }

    .countdown{
        gap:20px;
    }

    .time strong{
        font-size:34px;
    }

    .types-grid{
        grid-template-columns:
            1fr 1fr;
    }

    .features-grid{
        grid-template-columns:1fr;
    }

    .step{
        grid-template-columns:
            55px 1fr;

        gap:15px;
    }

    .step-no{
        font-size:38px;
    }

    .price{
        font-size:65px;
    }

    .offer-box{
        padding:55px 20px;
    }
}

@media(max-width:400px){

    .types-grid{
        grid-template-columns:1fr;
    }

    .hero h1{
        font-size:55px;
    }

    .demo-title{
        font-size:40px;
    }
}

</style>
</head>


<body>


<!-- =========================================
     FLOATING STARS
========================================= -->

<div id="stars"></div>


<!-- =========================================
     MUSIC
========================================= -->

<div class="music-bar">

    <div class="music-label">
        LISTEN WHILE YOU EXPLORE
    </div>

    <audio controls preload="metadata">

        <source
            src="tera naam doon.mp3"
            type="audio/mpeg"
        >

        Your browser does not support audio.

    </audio>

</div>


<!-- =========================================
     HERO
========================================= -->

<section class="hero">

    <div class="hero-content reveal">

        <div class="brand">
            LISKUN PRESENTS
        </div>

        <h1>

            DON'T JUST

            <span>
                SAY HAPPY BIRTHDAY.
            </span>

        </h1>

        <p class="hero-text">

            Give them something they didn't expect —
            a cinematic birthday website made specially
            for them.

        </p>

        <div class="hero-buttons">

            <a
                href="#experience"
                class="btn"
            >
                See The Experience
            </a>

            <a
                href="#order"
                class="btn"
            >
                Get Yours — ₹77
            </a>

        </div>

    </div>

    <div class="scroll">
        SCROLL TO DISCOVER
    </div>

</section>


<!-- =========================================
     EXPERIENCE
========================================= -->

<section
    class="experience"
    id="experience"
>

    <div class="container">

        <div class="center reveal">

            <div class="eyebrow">
                THE EXPERIENCE
            </div>

            <h2>

                A BIRTHDAY

                <span class="gold">
                    THEY'LL REMEMBER.
                </span>

            </h2>

        </div>


        <div class="demo-box reveal">

            <div class="demo-top">

                <span>
                    PRIVATE BIRTHDAY EXPERIENCE
                </span>

                <span>
                    MADE FOR ONE PERSON
                </span>

            </div>


            <div class="demo-title">

                Someone
                <br>
                Special.

            </div>


            <p class="demo-message">

                Imagine sending them a link on their birthday.

                They open it, hear their song, see their name,
                watch the countdown disappear and discover a
                message written only for them.

            </p>


            <div class="countdown">

                <div class="time">

                    <strong id="days">
                        00
                    </strong>

                    <small>
                        DAYS
                    </small>

                </div>


                <div class="time">

                    <strong id="hours">
                        00
                    </strong>

                    <small>
                        HOURS
                    </small>

                </div>


                <div class="time">

                    <strong id="minutes">
                        00
                    </strong>

                    <small>
                        MINUTES
                    </small>

                </div>


                <div class="time">

                    <strong id="seconds">
                        00
                    </strong>

                    <small>
                        SECONDS
                    </small>

                </div>

            </div>


            <a
                href="#order"
                class="btn"
            >
                I Want One Like This
            </a>

        </div>

    </div>

</section>


<!-- =========================================
     ATTENTION
========================================= -->

<section class="problem">

    <div class="container reveal">

        <div class="eyebrow">
            THINK ABOUT IT
        </div>

        <h2>

            A MESSAGE LASTS

            <span class="gold">
                A MINUTE.
            </span>

        </h2>

        <p>

            A birthday website can become
            a memory they can open again and again.

        </p>

    </div>

</section>


<!-- =========================================
     OFFER
========================================= -->

<section
    class="offer"
    id="order"
>

    <div class="offer-box reveal">

        <div class="eyebrow">
            YOUR TURN
        </div>

        <h2>

            YOUR PERSON

            <span class="gold">
                DESERVES MORE.
            </span>

        </h2>


        <div class="price">

            ₹77

            <small>
                / WEBSITE
            </small>

        </div>


        <p class="offer-description">

            Get a personalized cinematic birthday website
            created specially for someone you love.

            Your name.
            Their name.
            Their story.
            Their song.
            Their birthday.

        </p>


        <a
            href="#contact"
            class="btn"
        >
            Create My Website
        </a>

    </div>

</section>


<!-- =========================================
     WHO IS IT FOR
========================================= -->

<section>

    <div class="container">

        <div class="center reveal">

            <div class="eyebrow">
                MADE FOR THEM
            </div>

            <h2>

                WHO'S

                <span class="gold">
                    THE PERSON?
                </span>

            </h2>

        </div>


        <div class="types-grid reveal">


            <div class="type">

                <div class="type-number">
                    01
                </div>

                <div class="type-name">
                    Girlfriend
                </div>

            </div>


            <div class="type">

                <div class="type-number">
                    02
                </div>

                <div class="type-name">
                    Boyfriend
                </div>

            </div>


            <div class="type">

                <div class="type-number">
                    03
                </div>

                <div class="type-name">
                    Brother
                </div>

            </div>


            <div class="type">

                <div class="type-number">
                    04
                </div>

                <div class="type-name">
                    Sister
                </div>

            </div>


            <div class="type">

                <div class="type-number">
                    05
                </div>

                <div class="type-name">
                    Best Friend
                </div>

            </div>


        </div>

    </div>

</section>


<!-- =========================================
     FEATURES
========================================= -->

<section class="features">

    <div class="container">

        <div class="reveal">

            <div class="eyebrow">
                WHAT YOU GET
            </div>

            <h2>

                MORE THAN

                <span class="gold">
                    A WEBSITE.
                </span>

            </h2>

        </div>


        <div class="features-grid">


            <div class="feature reveal">

                <div class="feature-number">
                    01
                </div>

                <h3>
                    Cinematic Design
                </h3>

                <p>
                    A premium dark design created
                    to feel special from the first second.
                </p>

            </div>


            <div class="feature reveal">

                <div class="feature-number">
                    02
                </div>

                <h3>
                    Birthday Countdown
                </h3>

                <p>
                    A live countdown that builds
                    anticipation before the surprise.
                </p>

            </div>


            <div class="feature reveal">

                <div class="feature-number">
                    03
                </div>

                <h3>
                    Their Song
                </h3>

                <p>
                    Add a special song to make
                    the experience feel personal.
                </p>

            </div>


            <div class="feature reveal">

                <div class="feature-number">
                    04
                </div>

                <h3>
                    Personal Message
                </h3>

                <p>
                    Add your own letter, wishes,
                    memories and words.
                </p>

            </div>


            <div class="feature reveal">

                <div class="feature-number">
                    05
                </div>

                <h3>
                    Surprise Unlock
                </h3>

                <p>
                    Special sections can stay hidden
                    until the right moment.
                </p>

            </div>


            <div class="feature reveal">

                <div class="feature-number">
                    06
                </div>

                <h3>
                    Interactive
                </h3>

                <p>
                    Smooth animations and interactive
                    moments keep the experience engaging.
                </p>

            </div>


            <div class="feature reveal">

                <div class="feature-number">
                    07
                </div>

                <h3>
                    Mobile Friendly
                </h3>

                <p>
                    Designed to look beautiful on phones,
                    tablets and desktops.
                </p>

            </div>


            <div class="feature reveal">

                <div class="feature-number">
                    08
                </div>

                <h3>
                    Customized
                </h3>

                <p>
                    Names, dates, messages, colors
                    and content can be personalized.
                </p>

            </div>


        </div>

    </div>

</section>


<!-- =========================================
     HOW IT WORKS
========================================= -->

<section>

    <div class="container">

        <div class="center reveal">

            <div class="eyebrow">
                SIMPLE PROCESS
            </div>

            <h2>

                FROM IDEA

                <span class="gold">
                    TO SURPRISE.
                </span>

            </h2>

        </div>


        <div class="steps">


            <div class="step reveal">

                <div class="step-no">
                    01
                </div>

                <div>

                    <h3>
                        Contact Liskun
                    </h3>

                    <p>
                        Tell me who the website is for
                        and what kind of birthday
                        experience you want.
                    </p>

                </div>

            </div>


            <div class="step reveal">

                <div class="step-no">
                    02
                </div>

                <div>

                    <h3>
                        Send The Details
                    </h3>

                    <p>
                        Send the name, birthday date,
                        message, song and any special ideas.
                    </p>

                </div>

            </div>


            <div class="step reveal">

                <div class="step-no">
                    03
                </div>

                <div>

                    <h3>
                        I Create It
                    </h3>

                    <p>
                        Your information becomes
                        a personalized birthday website.
                    </p>

                </div>

            </div>


            <div class="step reveal">

                <div class="step-no">
                    04
                </div>

                <div>

                    <h3>
                        Send The Surprise
                    </h3>

                    <p>
                        Share the website with them
                        on their special day.
                    </p>

                </div>

            </div>


        </div>

    </div>

</section>


<!-- =========================================
     MEMORY
========================================= -->

<section class="memory">

    <div class="container">

        <div class="memory-card reveal">

            <div class="eyebrow">
                THE IDEA
            </div>

            <h3>

                DON'T GIVE THEM

                <span class="gold">
                    ANOTHER MESSAGE.
                </span>

            </h3>

            <p>

                Give them a moment.
                Give them something unexpected.
                Give them a website made only for them.

            </p>

        </div>

    </div>

</section>


<!-- =========================================
     CONTACT
========================================= -->

<section
    class="contact"
    id="contact"
>

    <div class="container reveal">

        <div class="eyebrow">
            READY?
        </div>

        <h2>

            LET'S MAKE

            <span class="gold">
                THEIR DAY.
            </span>

        </h2>


        <p class="contact-text">

            Want a custom birthday website for your
            girlfriend, boyfriend, brother, sister
            or best friend?

            Contact Liskun and let's create
            something special.

        </p>


        <a
            href="https://wa.me/919348424315"
            class="btn"
            target="_blank"
        >
            Contact Liskun — ₹77
        </a>


        <div class="contact-note">

            BIRAJA PRASAD JENA · LISKUN

        </div>

    </div>

</section>


<!-- =========================================
     FOOTER
========================================= -->

<footer>

    <strong>
        LISKUN
    </strong>

    <p>
        Custom Birthday Websites · ₹77
    </p>

</footer>


<script>

/* =========================================
   FLOATING STARS
========================================= */

const starContainer =
    document.getElementById("stars");

const starCount =
    window.innerWidth < 600
        ? 90
        : 150;


for(let i = 0; i < starCount; i++){

    const star =
        document.createElement("span");

    star.className = "star";


    const size =
        Math.random() * 2.4 + .5;


    star.style.width =
        size + "px";

    star.style.height =
        size + "px";


    star.style.left =
        Math.random() * 100 + "%";


    star.style.animationDuration =
        (Math.random() * 20 + 12)
        + "s";


    star.style.animationDelay =
        (Math.random() * -30)
        + "s";


    star.style.setProperty(
        "--drift",
        (Math.random() * 160 - 80)
        + "px"
    );


    star.style.opacity =
        Math.random() * .7 + .15;


    starContainer.appendChild(star);

}


/* =========================================
   DEMO COUNTDOWN
========================================= */

const birthday =
    new Date(
        "2026-11-05T00:00:00+05:30"
    );


function updateCountdown(){

    const now =
        new Date();


    let diff =
        birthday - now;


    if(diff < 0){

        diff = 0;

    }


    const days =
        Math.floor(
            diff /
            (1000 * 60 * 60 * 24)
        );


    const hours =
        Math.floor(
            (diff /
            (1000 * 60 * 60))
            % 24
        );


    const minutes =
        Math.floor(
            (diff /
            (1000 * 60))
            % 60
        );


    const seconds =
        Math.floor(
            (diff / 1000)
            % 60
        );


    document.getElementById("days")
        .textContent =
        String(days)
        .padStart(2,"0");


    document.getElementById("hours")
        .textContent =
        String(hours)
        .padStart(2,"0");


    document.getElementById("minutes")
        .textContent =
        String(minutes)
        .padStart(2,"0");


    document.getElementById("seconds")
        .textContent =
        String(seconds)
        .padStart(2,"0");

}


updateCountdown();

setInterval(
    updateCountdown,
    1000
);


/* =========================================
   SCROLL REVEAL
========================================= */

const observer =
    new IntersectionObserver(

        entries => {

            entries.forEach(entry => {

                if(entry.isIntersecting){

                    entry.target
                        .classList
                        .add("visible");

                    observer.unobserve(
                        entry.target
                    );

                }

            });

        },

        {
            threshold:.12
        }

    );


document
    .querySelectorAll(".reveal")
    .forEach(
        el =>
        observer.observe(el)
    );

</script>

</body>
</html>
