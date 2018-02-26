---
layout: post
title: "Dokumentácia k zadaniu 1."
date: 2018-02-25
---
**Prečítať si** [Znenie zadania](https://wiki.fiit.stuba.sk/study/bc/info/wp/2017-18/zadanie1/)
### Rozloženie stránok
* Štruktúra osobného portfólia je rozdelená na **header, content a footer**. Jednotlivé časti sú zadefinované v súbore `_layouts/default.html`.
1. Header tvorí nadpis, ktorý využíva premennú `page.title`. Súčasťou headera sú aj odkazy na štýlovacie súbory, ktoré definujú vzhľad webstránky.
V headeri sa nachádza aj navigácia, ktorá tam je vložená pomocou `{ % include nav.html % }`
2. Content je taktiež definovaný premennou `page.content` a nachádza sa v časti `<body></body>`.
3. Footer tvorí tiež includovaný súbor a to `{ % include footer.html % }`.

* Jednotlivé stránky majú __layout obsahu__ vytvorený individuálne a to v závislosti od konkrétneho obsahu.
  * __O mne__ obsahuje fotku autora webstránky + krátky úvod s informáciami pre návštevníka.
  Nižšiu časť tejto stránky tvoria __Aktuality__, kde sa nachádzajú najnovšie príspevky z blogu.
  * __Developerský profil__ je rozdelený na dve sekcie pomocou `html tabs` menu, __Profil developera__ a sekcia __Webové publikovanie__.
  Profil developera obsahuje prehľad o programovacích jazykoch ktoré ovládam a do akej miery + zoznam IT projektov na ktorých som doteraz pracoval.
  Webové publikovanie je tiež rozdelené na 3 časti, ktoré slúžia na dokumentáciu jednotlivých zadaní. Každá dokumentácia je vytvorená pomocou __markdown__.
  * __Burza__ je jedna zo stránok, ktorá je mojim koníčkom. Zobrazuje zoznam zaujímavých ľudí z tejto oblasti + nejakú literatúru.
  Všetky tieto informácie sú načítané z __data file__ vo formáte `.csv`.Tieto súbory sú uložené v zložke `_data/` <br /><br /> Ukážka jedného zo súborov (__books.csv__):
{% highlight csv %}
nadpis,autor,link
The art and science of technical analysis,Adam Grimes,https://books.google.sk/books?id=OmaeIdd95EQC&lpg=PP1&pg=PP1#v=onepage&q&f=false
Technická analýza na akciových menových a komoditních trzích,Jitka Veselá a Martin Oliva,https://www.martinus.sk/?uItem=223790
{%endhighlight%}
  * __Hobby__ dokumentuje moju novú záľubu - FPV Racing Drone. Pár fotiek + videí z doterajších pokusov a taktiež moja výbava je súčasťou tejto stránky.
  * __Fotogaléria__ zobrazuje nejaké fotografie, ktoré som nafotil kade tade vo svete.
<br /><br />
### Použité prvky v šablónach
* __5 premenných:__
  * `site, page, content, layout, site.posts, site.data, page.title`
* __5 filtrov / tagov:__
  * `baseurl, smartify, include, link, code highlighter`
* __kolekcie / dátové súbory:__
  * `data files 2x`
* __1 plugin:__
  *
<br /><br />
### Použité štýly
* Webstránka je štýlovaná pomocou `css` štýlov, kde každá stránka má vlastný súbor `.css` pre lepšiu prehľadnosť pri potrebe editovania vzhľadu/štýlov.
Súbory sa nachádzajú v zložke `css/`. Keďže dnes už existujú rôzne knižnice pre štýlovanie, bola by škoda nevyužiť to, a preto sú v súbore `_layouts/default.html` v časti `<head></head>`
nalinkované potrebné súbory pre __bootstrap__, ktorý tvorí podstatnú časť štýlovania.
