<script>
    export let state;

    export let page = 0;

    function generatePage(page_) {
        page = page_;
    }
</script>

<div class="bottomNav {!state ? 'bFocus' : ''}">
    <div
        class="home {page === 0 ? 'focus' : ''}"
        on:click={() => generatePage(0)}
    >
        <div class="home-i" />
    </div>
    <div
        class="posts {page === 1 ? 'focus' : ''}"
        on:click={() => generatePage(1)}
    >
        <div class="posts-i" />
    </div>
    <div
        class="profile {page === 2 ? 'focus' : ''}"
        on:click={() => generatePage(2)}
    >
        <div class="profile-i" />
    </div>
</div>

<style>
    @media (prefers-color-scheme: dark) {
        :root {
            --color: white;
            --homeUrl: url("./../home.png");
            --postUrl: url("./../post.png");
            --profileUrl: url("./../profile.png");
        }
    }

    @media (prefers-color-scheme: light) {
        :root {
            --color: black;
            --homeUrl: url("./../home_B.png");
            --postUrl: url("./../post_B.png");
            --profileUrl: url("./../profile_B.png");
        }
    }

    .bottomNav {
        width: 100%;
        height: 10vh;
        position: absolute;
        bottom: 0;
        transition: ease-in-out 0.4s;

        display: flex;
        flex-direction: row;
    }

    .bFocus {
        margin-bottom: -10vh;
    }

    .home,
    .profile {
        width: 2rem;
        height: 2rem;

        transition: ease-in-out 0.2s;

        padding: 1%;

        margin:auto;
    }

    .posts {
        width: 2rem;
        height: 2rem;
        margin:auto;

        display: flex;
        align-items: center;
        justify-content: center;

        transition: ease-in-out 0.2s;

        padding: 1%;
    }

    .focus {
        border-bottom: 2px solid #5533ebde;
    }

    .home-i {
        width: 100%;
        height: 100%;
        background-image: var(--homeUrl);
        background-size: 90% 90%;
        background-repeat: no-repeat;
        background-position: center;
    }

    .profile-i {
        width: 100%;
        height: 100%;
        background-image: var(--profileUrl);
        background-size: 75% 75%;
        background-repeat: no-repeat;
        background-position: center;
    }

    .posts-i {
        width: 100%;
        height: 100%;
        background-image: var(--postUrl);
        background-size: 80% 80%;
        background-repeat: no-repeat;
        background-position: center;
        rotate: 45deg;
    }
</style>
