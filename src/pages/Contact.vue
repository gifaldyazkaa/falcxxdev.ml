<template>
    <section class="container section" id="contactme">
        <div id="title">
            <h2 class="section__title">Contact Me</h2>
            <hr />
        </div>
        <div class="description">
            <p>
                You can reach me out via email at <a :href="`mailto:${myself.email}`">{{ myself.email }}</a> or via
                socials below :
            </p>
        </div>
        <div class="image-container">
            <div v-for="s in socials">
                <SocialButton :name="s.name" :bg="s.bg" :color="s.color" :dest="s.url" />
            </div>
            <br />
            <div></div>
        </div>

        <br />
        <div id="we-hate-form-input">
            <p>
                Where is the form input? No. I'm not using form input <s>cuz it's cringe</s>.
                <br />
                Reach me via email or socials instead of using form input.
            </p>
        </div>
        <div id="discord">
            <h2 id="discord-title">Me at Discord</h2>
            <a :href="`https://discord.com/users/${discordCard.userId}`">
                <img
                    id="discord-card"
                    :src="`https://lanyard-profile-readme.vercel.app/api/${discordCard.userId}?theme=light`"
                    :alt="discordCard.altText"
                />
            </a>
        </div>
        <div id="game">
            <h2 id="game-title">Play with me</h2>
            <div class="image-container">
                <div v-for="g in games">
                    <ul>
                        <li class="list game-badge">
                            <strong>{{ g.name }}</strong> - UID: <code>{{ g.id }}</code
                            >. {{ g.more }}
                        </li>
                    </ul>
                </div>
            </div>
        </div>
        <div id="credits">
            <h2 id="credits-title">Credits</h2>
            <p id="desc">
                I used their fan-art in this website. So, here is some credits for those people who created the art.
                Thanks~!
            </p>
            <div id="list" v-for="c in credits">
                <ul>
                    <li class="list">
                        {{ c.type }} is drawn by
                        <a :href="`https://twitter.com/${c.username}`">{{ c.artist }}</a>
                        | <a :href="c.tweets">See tweet</a>
                    </li>
                </ul>
            </div>
        </div>
    </section>
</template>

<script lang="ts">
import SocialButton from '../components/SocialButton.vue';
import myself from '../data/self';
import socials from '../data/socials';
import games from '../data/games';
import discordCard from '../data/discordCard';
import credits from '../data/credits';

export default {
    data() {
        return {
            myself,
            socials,
            games,
            discordCard,
            credits,
        };
    },
    components: { SocialButton },
};
</script>

<style lang="scss">
@import '../styles/variable';
@import '../styles/anchor';
// Base
h2,
p {
    cursor: default;
    font-family: $lexend;
}
img {
    pointer-events: none;
}
// Main section
.section__title {
    font-family: 'Lexend', sans-serif;
}
.description p {
    margin-top: 15px;
}
li {
    &.list {
        font-family: $lexend;
        list-style: disc;
        margin-left: 18px;
        cursor: default;
    }
}
#we-hate-form-input p {
    margin-top: 10px;
    font-size: 12px;
}
// Credits section
#discord-title,
#game-title,
#credits-title {
    margin-top: 15px;
    color: var(--title-color);
}
#credits {
    #desc {
        margin-top: 3px;
        margin-bottom: 5px;
        font-size: 13px;
    }
    #list {
        margin-top: 3px;
        font-size: 14px;
        padding-bottom: 90px;
    }
}
#discord-card {
    margin-top: 9px;
}
.game-badge {
    margin-right: 3px;
    margin-top: 5px;
    margin-right: 5px;
}
</style>
