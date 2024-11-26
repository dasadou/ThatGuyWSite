<script>
    import CVSection from "$lib/CVSection.svelte";

    let firstName = "Ayoub";
    let lastName = "Chihab";
    let summary = [
        " Diplômé en génie logiciel de Polytechnique Montréal en génie logiciel à Polytechnique Montréal, ayant une volonté d’apprentissage et de rester à jour."
        , "Expérience en programmation, gestion de projets et travail d’équipe.,"
        , " Prêt à relever des défis et fournir des solutions logicielles de qualité.,"
    ]
    let experiences = [];
    let projects = [];
    let formations = [];
    let skills = [];

</script>

<div id="CV">
    <div id="name">

        <h1 class="generic" id="first-name">{firstName} </h1>
        <h1 class="generic" id="last-name">{lastName}</h1>
    </div>

    <div id="contact-info">
        <p class="generic" id="e-mail">✉ ayoub.chihab.aychi@gmail.com | </p>
        <p class="generic" id="phone-number">+1 (438) 528-8545 |</p>
        <p class="generic" id="address">522 11e Avenue, H7N 4C6, Laval, QC, Canada</p>
    </div>
    <h2>Sommaire</h2>
    <ul class="section" id="Sommaire">
        <CVSection content="{summary}"></CVSection>
    </ul>
    <h2>Experience</h2>
    <ul class="section" id="Experience">

    </ul>

    <h2>Projet Universitaire</h2>
    <ul class="section" id="Projet">
        <CVSection
                title="Application Web d'ACV"
                date="janvier 2024 - avril 2024"
                skills={['TypeScript', 'HTML', 'CSS', 'Python']}
                content={[
     "Conçu et développé une application web pour un logiciel d’analyse de cycle de vie en collaboration avec une équipe. Frontend en Angular et backend en Python"
    ,"Créé un serveur Python utilisant le framework FastAPI pour développer une API RESTful. Tests effectués avec PyTest" 
    ,"Utilisé Docker pour containeriser les builds web et serveur"]}
        ></CVSection>
    </ul>

    <h2>Formation</h2>
    <ul class="section" id="Formation">
        <CVSection title="Baccalauréat en ingénierie en Génie logiciel" location="Polytechnique Montréal"
                   date="janvier 2020 – août 2024"></CVSection>
    </ul>
    <h2>Competence</h2>
    <ul class="section" id="Competence">
        <CVSection></CVSection>
    </ul>

</div>
<style>
    #name {
        font-family: arial, serif;
        font-size: 24px;
        color: #1d76e2;
    }

    #first-name {
        font-weight: bold;
    }

    .generic {
        display: inline;
    }

    h2 {
        font-family: arial, serif;
        font-size: 16px;
        color: #1d76e2;
    }

    #CV {
        padding: 20px;
        outline-color: black;
        outline-style: solid;
        margin-left: 10px;
        margin-right: 10px;
    }
</style>

