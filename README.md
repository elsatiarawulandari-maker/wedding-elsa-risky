# wedding-elsa-risky
Website Undangan Pernikahan Elsa &amp; Risky
// ===============================
// Wedding Elsa & Risky
// ===============================

// Tombol buka undangan + musik
const openBtn = document.getElementById("openInvitation");
const music = document.getElementById("music");

if(openBtn){
    openBtn.addEventListener("click", function(){

        document.querySelector(".cover").style.display="none";

        if(music){
            music.play().catch(()=>{
                console.log("Browser meminta interaksi pengguna.");
            });
        }

        window.scrollTo({
            top:0,
            behavior:"smooth"
        });

    });
}

// ===============================
// COUNTDOWN
// ===============================

const targetDate = new Date("March 20, 2027 08:00:00").getTime();

const timer = setInterval(function(){

    const now = new Date().getTime();

    const distance = targetDate-now;

    if(distance<0){

        clearInterval(timer);

        document.getElementById("timer").innerHTML="Acara Sedang Berlangsung";

        return;

    }

    const days=Math.floor(distance/(1000*60*60*24));

    const hours=Math.floor((distance%(1000*60*60*24))/(1000*60*60));

    const minutes=Math.floor((distance%(1000*60*60))/(1000*60));

    const seconds=Math.floor((distance%(1000*60))/1000);

    document.getElementById("days").innerHTML=days;
    document.getElementById("hours").innerHTML=hours;
    document.getElementById("minutes").innerHTML=minutes;
    document.getElementById("seconds").innerHTML=seconds;

},1000);

// ===============================
// COPY DANA
// ===============================

function copyDana(){

    navigator.clipboard.writeText("083189710428");

    alert("Nomor DANA berhasil disalin.");

}

// ===============================
// ANIMASI SCROLL
// ===============================

const observer = new IntersectionObserver(entries=>{

    entries.forEach(entry=>{

        if(entry.isIntersecting){

            entry.target.classList.add("show");

        }

    });

});

document.querySelectorAll("section").forEach(section=>{

    observer.observe(section);

});

// ===============================
// Efek muncul
// ===============================

const style=document.createElement("style");

style.innerHTML=`

section{

opacity:0;

transform:translateY(40px);

transition:1s;

}

section.show{

opacity:1;

transform:translateY(0);

}

`;

document.head.appendChild(style);
