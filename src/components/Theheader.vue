<script setup>

</script>

<template>
    <header>
        <nav>
            <ul>
                <li>
                    <a @click.self.prevent href="">
                        Home
                    </a>
                </li>
                <li>
                    <a @click.self.prevent href="">
                        About
                    </a>
                </li>
                <li>
                    <a @click.self.prevent href="">
                        Map
                    </a>
                </li>
                <li>
                    <a @click.self.prevent href="">
                        Contact
                    </a>
                </li>
            </ul>
        </nav>
    </header>
</template>

<style lang="scss" scoped>

header{
    width: 100vw;
    display: flex;
    align-items: center;
    justify-content: center;
    backdrop-filter: blur(10px);
    nav{
        display: flex;
        font-family: "Barlow Condensed", serif;
        font-weight: 700;
        font-style: normal;
        font-size: 24px;
        text-transform: uppercase;
        color: white;
        ul{
            display: flex;
            gap: 50px;
            li{
                list-style: none;
                a{
                    text-decoration: none;
                    color: white;
                    &:hover{
                        text-decoration: underline;
                        text-underline-offset: 5px;
                        text-decoration-thickness: 2px;
                        text-decoration-color: white;
                        text-underline-position: under;
                    }
                }
            }
        }
    }
}

</style>
