<style>
    .bannerIcon {
        vertical-align: -0.2em;
        font-size: 25px !important;
    }
    @font-face {
        font-family: 'Phantom Sans';
        src: url('https://assets.hackclub.com/fonts/Phantom_Sans_0.7/Bold.woff')
            format('woff'),
            url('https://assets.hackclub.com/fonts/Phantom_Sans_0.7/Bold.woff2')
            format('woff2');
        font-weight: bold;
        font-style: normal;
        font-display: swap;
    }

    #zoo_linkBanner {
        background-color: rgb(14, 77, 146);
        padding: clamp(8px, 2vw, 10px);
        text-align: center;
        vertical-align: center;
        position: fixed;
        left: 0;
        right: 0;
        top: 0;
        height: auto;
        min-height: 50px;
        z-index: 1000;
        font-size: clamp(14px, 3vw, 20px);
        transition: box-shadow 0.3s ease-in-out;
        font-family: Phantom Sans, sans-serif;
        text-decoration: none;
        color: white;
    }

    #zoo_linkBanner h1 {
        font-size: clamp(14px, 3vw, 20px);
        margin: 0;
        line-height: 1.3;
        padding: clamp(6px, 1vw, 8px) 0;
    }

    #zoo_linkBanner:hover {
        cursor: pointer;
        box-shadow: 0px 0px 50px 10px rgba(0, 25, 72, 0.551);
    }

    @media (max-width: 640px) {
        #zoo_linkBanner {
            min-height: 45px;
            padding: clamp(6px, 1.5vw, 8px);
        }

        .bannerIcon {
            font-size: clamp(16px, 2.5vw, 20px) !important;
        }
    }
</style>

<a href = "https://zoo.hackclub.com"><div id="zoo_linkBanner">
    <h1>CHECK OUT MORE AT THE ZOO <span class="material-symbols-outlined bannerIcon">pets</span> </h1>
</div></a>
