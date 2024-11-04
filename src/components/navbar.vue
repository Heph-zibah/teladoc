<script setup></script>

<template>
    <header class="header_container">
        <div class="header_section">
            <div class="header_logo">
                <a href="#"><img src="../assets/teledoc-logo.svg" alt="teledoc logo"></a>
            </div>
            <div class="header_language">
                <img src="../assets/globe-icon.svg" alt="globe icon">
                <span>ENG</span>
            </div>
        </div>
    </header>
</template>



<style scoped>
.header_container {
    max-width: 1240px;
    margin: auto;
    border-bottom: 1px solid #00000052;
    margin-top: 40px;
}
.header_section {
     display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0px 20px 5px 40px;
}
.header_logo{
    width: 140px;
    padding-left: 18px;
}
.header_language {
    display: flex;
    align-items: center;
    font-weight:700;
    gap: 4px;
}
.header_language img{
    width:40px;
}
</style>