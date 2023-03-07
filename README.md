## Napomena za plugine
Ako se plugin sprema kao .tgz file, proces je konceptualno isti kao kod kreiranja običnih paketa:
u rootu repozitorija (gdje se nalazi package-json)
1. `npm install`
2. `npm build` za kreiranje dist foldera
3. `npm pack` za kreiranje .tgz filea
4. Nastavi na Postavljanje paketa

Ako se ne sprema kao release, već se u projektu koji ga koristi izravno dohvaća preko repozitorija, notacijom `"app-details-opener": "SpinOsijek/app-details-opener"`, ključne su dvije stvari:
1. **dist ne smije biti u gitignoreu**; on mora biti uploadan na repozitorij. Ovo je bitno jer po defaultu on je u gitignoreu.
2. package.json plugina mora sadržati key `files` s bar ovim vrijednostima, na primjeru AppDetailsOpenera: `[
    "android/src/main/",
    "android/build.gradle",
    "dist/",
    "ios/Plugin/",
    "AppDetailsOpener.podspec"
  ]`
To definira koji fileovi će se dovući u `node_modules` nakon instaliranja preko `npm install`.
Kad se plugin kreira preko `npm init @capacitor/plugin@latest` package-json već je tako konfiguriran, ali dobro je znati u slučaju forkanja plugina, ili ako iz bilo kojeg razloga konfiguracija nije već takva.

# Postavljanje paketa
1. U Releases odjeljku klikni na željeni release ![1](/assets/Releases.jpg)
2. Klikom na olovku, uđi u uređivanje releasea ![2](/assets/EditRelease.jpg)
3. Ako radiš update postojećeg paketa, prvo ga ukloni iz releasea klikom na X uz postojeći paket
4. Drag-drop .tgz file paketa u Attach binaries polje
![3](/assets/Replace.jpg)
5. Na kraju, klik na Update release na dnu ekrana da se promjene spreme ![4](/assets/Update.jpg)

Desni klik -> Copy link address na neki od paketa na slici ![5](/assets/Replace.jpg) predstavlja link koji ide u package-json za instalaciju paketa
