<template>
    <footer class="footer_container">
        <div class="footer_section">
            <div class="copyright">
                <p>© 2002-2024 Teladoc, Inc. All rights reserved.</p>
            </div>
            <ul class="footer_links">
                <li><a href="#">Terms of Service</a></li>
                <li><a href="#">Notice of Privacy Practices</a></li>
                <li><a href="#">Notice of Non-Discrimination and Language Assistance</a></li>
            </ul>
            
        </div>
    </footer>
</template>

<style scoped>
.footer_container {
    max-width: 1100px;
    margin: auto;
    border-top: 1px dashed #727069;
    margin-top: 50px;
    margin-bottom: 40px;
}
.footer_section {
    text-align: center;
    display: flex;
    flex-direction: column-reverse;
    align-items: center;
    justify-content: center;
    gap: 16px;
    font-size: 13px;
    
    
    padding-top: 20px;

}
.footer_links li {
   
    margin-top: 16px;
}
.footer_links a {
    color:#5b2f91;
    font-weight: 700;
}

.copyright{
    color: #727069;
    margin-top: 14px;
}

@media screen and (min-width: 768px) {
    .footer_section {
    
    flex-direction: row;
    

}
.footer_links {
    display: flex ;
    gap:20px
}
}
</style>