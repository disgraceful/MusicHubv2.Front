<template>
    <v-card id="playlist-card" flat>
        <v-card-media :src="playlist.imgPath" height="220px">
            <v-btn relative fab left medium color="pink" class="fab-icon">
                <v-icon medium>favorite_border</v-icon>
            </v-btn>
            <v-btn relative fab left medium color="yellow" class="fab-icon">
                <v-icon medium>play_arrow</v-icon>
            </v-btn>
        </v-card-media>
        <v-card-title>
            <div>
                <router-link :to="{name:'Playlist',params:{username:user.username,id:playlist.id}}" tag="div" class="playlist-text">
                    {{playlist.name}}
                </router-link>
                <div class="grey--text">{{playlist.songAmount}} songs
                    <span v-if="playlist.rating>=0">, {{playlist.rating}} likes</span>
                </div>
            </div>
        </v-card-title>
    </v-card>
</template>

<script>
    export default {
        computed: {
            user() {
                var user = JSON.parse(window.localStorage.getItem('user'))
                if (user) {
                    return user;
                } else {
                    return "";
                }
            }
        },
        props: ['playlist']
    }
</script>

<style scoped>
    .playlist-text {
        color: black !important;
        cursor: pointer;
    }

    .playlist-text:hover {
        color: red !important;
    }

    #playlist-card {
        padding: 10px;
        border: 2px solid transparent;
    }

    #playlist-card:hover {
        border: 2px solid;
        border-color: yellow;
    }

    .fab-icon {
        top: 80px;
        left: 60px;
        display: none;
    }

    #playlist-card:hover .fab-icon {
        display: flex;
    }
</style>