<script lang="ts">
        import shell from "../lib/about/shell.svg";
    import renew from "../lib/about/renew.png";
    let img: HTMLDivElement, des: HTMLDivElement, element;

    function zoom() {
        des.style.transform = "scale(1.05)";
        des.style.transition = "all 0.5s";
    }

    function zoomout() {
        des.style.transform = "scale(1)";
        des.style.transition = "all 1s";
    }

    function zoom1() {
        img.style.transform = "scale(1.05)";
        img.style.transition = "all 0.5s";
    }

    function zoomout1() {
        img.style.transform = "scale(1)";
        img.style.transition = "all 1s";
    }

    function entry() {
        img.style.transform = "translateY(0em)";
        des.style.transform = "translateY(0em)";
        console.log("hai");
    }

    function exit() {}

    let observer: IntersectionObserver | null = null;

    function viewport(element: HTMLElement) {
    if (typeof IntersectionObserver !== "undefined") {
        observer = new IntersectionObserver((entries) => {
            entries.forEach((entry) => {
                const event = entry.isIntersecting ? "entry" : "exit";
                entry.target.dispatchEvent(new CustomEvent(event));
            });
        });
    
            observer.observe(element);
        } else {
            // Fallback behavior for environments without IntersectionObserver
            console.warn(
                "IntersectionObserver is not supported on this environment.",
            );
            // You might want to handle the case where IntersectionObserver is not available.
        }
    }
</script>

<main>
    <div class="wrap" use:viewport on:entry={entry} on:exit={exit}>
        <!-- svelte-ignore a11y-no-static-element-interactions -->
    <div
            class="description"
            bind:this={des}
            on:mouseenter={zoom}
            on:mouseleave={zoomout}
        >
            <p>
                Shell Eco-marathon is one of the world’s leading
                energy-efficiency engineering programmes for students. It aims
                to push the boundaries of what is technically possible and
                inspire young people to become leading scientists and engineers
                of future energy solutions. <br /><br />
                The programme provides a platform for high school and university
                teams to explore every aspect of design and technology, using their
                Science, Technology, Engineering, and Maths (STEM) skills to build
                their own ultra-energy-efficient cars, and then take them out on
                the track in competition. <br /><br />
                This time we team <span>ReNew</span> representing
                <a href="https://www.kct.ac.in/"
                    >Kumaraguru College of Technology</a
                > are participating in this prestegious competetion to show what
                our institution can bring out.
            </p>
    </div>
    <!-- svelte-ignore a11y-no-static-element-interactions -->
        <div
            class="images"
            bind:this={img}
            on:mouseenter={zoom1}
            on:mouseleave={zoomout1}
        >
            <div><img src={shell} alt="" /></div>
            <div><img src={renew} alt="" /></div>
        </div>
    </div>
</main>

<style>
@import url("https://fonts.googleapis.com/css2?family=DM+Serif+Display&family=Poppins:wght@300&display=swap");
    main {
        display: grid;
        justify-content: center;
        align-content: center;
        padding-top: 6em;
        padding-bottom: 10em;
    }
    .wrap {
        font-family: "Poppins", sans-serif;
        width: 80vw;
        display: flex;
        gap: 2em;
        flex-wrap: wrap;
        justify-content: center;
            }
    .description {
                height: fit-content;
        width: 40em;
        background-color: #354555;
        color: white;
        font-weight: 500;
        border-radius: 3em;
        padding: 2em;
        transform: translateY(7em);
        transition: all 2s;
    }
    .description:hover {
        transform: translateX(2em);
    }
    .description>p{
        font-size: 1.3em;
    }
    .images {
        height: 20em;
        width: 12em;
        display: grid;
        align-items: center;
        background-color: aquamarine;
        padding: 2em;
        border-radius: 3em;
        transform: translateY(7em);
        transition: all 3s;
    }

    span {
        font-weight: 900;
    }

    a {
        text-decoration: none;
        color: rgb(117, 128, 190);
        font-weight: 900;
    }
</style>
