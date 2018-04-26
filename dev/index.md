---
layout: default
title: "Webové publikovanie"
date: 2018-02-25
---
### Zadanie 1
**Prečítať si** [Znenie zadania](https://wiki.fiit.stuba.sk/study/bc/info/wp/2017-18/zadanie1/)
#### Rozloženie stránok
* Štruktúra osobného portfólia je rozdelená na **header, content a footer**. Jednotlivé časti sú zadefinované v súbore `_layouts/default.html`.
1. Header tvorí nadpis, ktorý využíva premennú `page.title`. Súčasťou headera sú aj odkazy na štýlovacie súbory, ktoré definujú vzhľad webstránky.
V headeri sa nachádza aj navigácia, ktorá tam je vložená pomocou `{ % include nav.html % }`
2. Content je taktiež definovaný premennou `page.content` a nachádza sa v časti `<body></body>`.
3. Footer tvorí tiež includovaný súbor a to `{ % include footer.html % }`.


* Jednotlivé stránky majú __layout obsahu__ vytvorený individuálne a to v závislosti od konkrétneho obsahu. Všeobecne sú vytvorené layouty pre všetky stránky, layout `default.html`, pre blog `post.html` a pre galériu `gallery.html`.
  * __O mne__ obsahuje fotku autora webstránky + krátky úvod s informáciami pre návštevníka.
  Nižšiu časť tejto stránky tvoria __Aktuality__, kde sa nachádzajú najnovšie príspevky z blogu.
  * __Webové publikovanie__ je rozdelené na 3 časti, ktoré slúžia na dokumentáciu jednotlivých zadaní. Každá dokumentácia je vytvorená pomocou __markdown__.
  * __Hobby__ dokumentuje moju novú záľubu - FPV Racing Drone. Pár fotiek + videí z doterajších pokusov a taktiež moja výbava je súčasťou tejto stránky.
  * __Fotogaléria__ zobrazuje nejaké fotografie, ktoré som nafotil kade tade vo svete.
  * __Burza__ je jedna zo stránok, ktorá je mojim koníčkom. Zobrazuje zoznam zaujímavých ľudí z tejto oblasti + nejakú literatúru.
  Všetky tieto informácie sú načítané z __data file__ vo formáte `.csv`.Tieto súbory sú uložené v zložke `_data/` <br /><br /> Ukážka jedného zo súborov (__books.csv__):
{% highlight csv %}
nadpis,autor,link
The art and science of technical analysis,Adam Grimes,https://books.google.sk/books?id=OmaeIdd95EQC&lpg=PP1&pg=PP1#v=onepage&q&f=false
Technická analýza na akciových menových a komoditních trzích,Jitka Veselá a Martin Oliva,https://www.martinus.sk/?uItem=223790
{%endhighlight%}

#### Použité prvky v šablónach
* __5 premenných:__
  * `site, page, content, layout, site.posts, site.data, page.title`
* __7 filtrov / tagov:__
  * `baseurl, smartify, include, link, code highlighter, date_to_string, number_of_words`
* __kolekcie / dátové súbory:__
  * `data files 2x`
* __1 plugin:__
  * `emoji_for_jekyll`
<br />

#### Použité štýly
* Webstránka je štýlovaná pomocou `css` štýlov, kde každá stránka má vlastný súbor `.css` pre lepšiu prehľadnosť pri potrebe editovania vzhľadu/štýlov.
Súbory sa nachádzajú v zložke `css/`. Keďže dnes už existujú rôzne knižnice pre štýlovanie, bola by škoda nevyužiť to, a preto sú v súbore `_layouts/default.html` v časti `<head></head>`
nalinkované potrebné súbory pre __bootstrap__, ktorý tvorí podstatnú časť štýlovania.

### Zadanie 2
  **Prečítať si** [Znenie zadania](https://wiki.fiit.stuba.sk/study/bc/info/wp/2017-18/zadanie2/)

#### Použité elementy a atribúty
* __štandardné členenie textu na kapitola, podkapitola, podpodkapitola, príloha, generovaný obsah:__
  * Obsah sa generuje automaticky (štandard Docbook nastavení), ak to nie je "overridnuté" v konfiguračnom súbore

    {% highlight html %}
    <chapter>
      <title>Nazov kapitoly</title>
      <para> Text odstavca ... </para>
      <section>
        <title>Nadpis podkapitoly</title>
        <para> Text podkapitoly </para>
          <section>
            <title>Nadpis podpodkapitoly</title>
            <para> Text podpodkapitoly </para>
          </section>
        </section>
      </chapter>{% endhighlight %}
      {% highlight html %}
        <appendix>
          <title>Prílohy</title>
          <para>
            CD médium, na ktorom sa nachádzajú všetky súbory potrebné na spustenie projektu na počítači.
            </para>
        </appendix>{% endhighlight %}

* __zvýraznenie slov, zvýraznenie členenia textu odrážkami alebo číslovaním:__
  * zvýraznenie slov `<emphasis>kurziva</emphasis>` alebo `<emphasis role="strong">tucne pismo</emphasis>`
  * členenie textu odrážkami
  * členenie textu číslovaním
  * custom nastavenie pre pridanie prázdneho riadku pomocou `<?linebreak?>`, tento príkaz je manuálne definovaný nasledovne:
    {% highlight html %}
    <xsl:template match="processing-instruction('linebreak')">
      <fo:block><fo:leader/></fo:block>
    </xsl:template>{% endhighlight %}


  {% highlight html %}
  <itemizedlist mark='bullet'>
      <listitem>
        <para>INIT - vytvorí Z-spojenie</para>
      </listitem>
      <listitem>
        <para>SEARCH - umožní klientovi vykonávať dopyty</para>
      </listitem>
      <listitem>
        <para>PRESENT - klient požiada server o výsledky hľadania</para>
      </listitem>
    </itemizedlist>

    <orderedlist numeration="arabic">
      <listitem>
        <para>Formát pre autority</para>
      </listitem>
      <listitem>
        <para>Bibliografický formát</para>
      </listitem>
      <listitem>
        <para>Formát pre klasifikačné záznamy</para>
      </listitem>
      <listitem>
        <para>Formát pre komunitné informácie</para>
      </listitem>
      <listitem>
        <para>Formát pre holdingové záznamy</para>
      </listitem>
    </orderedlist>{% endhighlight %}
* __odkazy na iné časti vlastného dokumentu, prípadne odkazy na URL:__
  * `<link endlink="id_odkazovanej_casti">text odkazu</link>` alebo `<ulink url="http://www.infolib.sk/sk/informacie/verejne-kniznice/zakladne-udaje/"></ulink>`
* __poznámka pod čiarou:__
  * `<footnote><para>Pripojiť sa na tieto databázy je možné prostredníctvom Z-klienta, čiže spojenia podľa <emphasis>protokolu Z39.50</emphasis>.</para></footnote>`
* __zoznam použitej literatúry a zdrojov vrátane ich citácie v texte:__
  * Na označenie citácie je použité číslo na konci vety `<citation>8</citation>` ktoré je týmto kódom ohraničené `[8]`
  * Vytvorenie bibliografie na konci dokumentu
    {% highlight html %}
      <bibliography>
        <title>Použitá literatúra</title>

        <bibliomixed><abbrev>1</abbrev> InfoLib.sk.: <title>Knižničný systém v Slovenskej republike</title>.
        <bibliomisc>Získané z WWW: <ulink url="http://www.infolib.sk/sk/informacie/verejne-kniznice/zakladne-udaje/"></ulink></bibliomisc></bibliomixed>
      </bibliography>{% endhighlight %}
* __vloženie obrázku a tabuliek, odkazy na ne v texte; zoznam obrázkov a tabuliek v úvode alebo závere textu:__
  * Zoznam obrázkov a tabuliek je na začiatku a je generovaný automaticky ako obsah ak to nie je definované inak. Je to štandard pre typ `book`. Vytvorenie tabuľky je podobné
    ako v html, pridanie obrázku je iné:
  {% highlight html %}
  <figure id="vlcata">
        <title>Náhľad portálu Vĺčatá.sk – hlavná stránka.</title>
        <mediaobject>
          <imageobject condition="web">
            <imagedata fileref="img/vlcata.png" format="PNG" scale="37"/>
          </imageobject>
          <imageobject condition="print">
            <imagedata fileref="img/vlcata.pdf" format="PDF"/>
          </imageobject>
          <textobject>
            <phrase>Náhľad portálu Vĺčatá.sk – hlavná stránka.</phrase>
          </textobject>
        </mediaobject>
      </figure>{% endhighlight %}

* __vytvorenie registra pojmov (indexu) s pojmami hierarchicky usporiadanými do dvoch úrovni:__
  * Pridanie indexu je namáhavé pretože treba manuálne označovať jednotlivé indexy v texte diela a to napríklad takto: `<indexterm><primary>štandardy</primary><secondary>Z39.50</secondary></indexterm>`.
  * Následne je len potrebné zavolať `<index/>` niekde v dokumente, kde chceme aby sa zobrazil zoznam indexov so stranou ich výskytu.

### Zadanie 3
  **Prečítať si** [Znenie zadania](https://wiki.fiit.stuba.sk/study/bc/info/wp/2017-18/zadanie3/)
* Opis typu dokumentu + opis účelu navrhnutých elementov
  * __V súbore ppt.dtd sa nachádza DTD:__
    * Ukážka:
    {% highlight DTD %}
<!-- root, kazda ppt ma najmenej 1 slajd -->
<!ELEMENT ppt (slide*)>
<!-- kazdy slide ma nadpis, ostatne su volitelne, left a right su na vytvorenie dvoch stlpcov v slajde (napr obrazok napravo a text nalavo -->
<!ELEMENT slide (title, ((univ?, fac?, auth*)* | (text* | list* | p* | image*) | (left? , right?)*)*)>
<!ATTLIST slide type (title|full_screen|split_screen|ref) #REQUIRED>
<!-- pozadie slajdu moze byt grey alebo white -->
<!ATTLIST slide color (grey|white) #IMPLIED>
<!-- nadpis -->
<!ELEMENT title (#PCDATA)>
{% endhighlight %}

* Vytvorenie ukážkovej XML prezentácie demonštrujúcej možnosti definície typu dokumentu
  * Prezentácia vo forme XML sa nachádza v súbore ppt.xml kde sú použité / demonštrované možnosti DTD
    * Prezentácia má základnú štruktúru, ktorú definuje `<slide></slide>` ktorý vytvára jeden samostatný slajd.
      V slajde sa nachádzajú všetky možné vnorené elementy ako to povoľuje DTD. Môže to byť napríklad obyčajný `text`, `p`, `image`, `list`, `title` a podobne.
      Prezentácia má 2 typy slajdov, a to preto aby bolo možné zobraziť text alebo obrázky aj vedľa seba. Jeden typ je `full_screen`, ktorý využíva plnú veľkosť/rozmery slajdu,
      druhý typ je `split_screen`, ktorý rozdeľuje priestor slajdu na 50%.
* Základný návrh XSL transformácií, ich vhodnosť, parametrizácia
  * V súbore general.xsl sa nachádzajú XLS transformácie, ktoré sú všeobecne použiteľné a je možné nastaviť parametre podľa potreby, ktoré saa aplikujú všade, kde sa využívajú.
  {% highlight xsl %}
  <xsl:variable name="p-size" select="'20'" ></xsl:variable>
  <xsl:variable name="list-item-size" select="'22'" ></xsl:variable>
  <xsl:variable name="ref-size" select="'22'" ></xsl:variable>
  <xsl:variable name="title-size" select="'36'" ></xsl:variable>{% endhighlight %}
* XSLT pre konverziu prezentácie z XML -> XHTML+CSS
  * Nachádza sa v súbore `html.xsl` a `css` sa nachádza v `ppt.css`.
  * Podobne ako tento `template` pre slide, sú tvorené aj ostatné, ktoré nadväzujú na štruktúru `ppt.xml` a `DTD`. Atribút `match` požaduje parameter, ktorý určuje, o aký typ slajdu sa jedná.
V tomto prípade je to `full_screen`. Nasleduje obsah tohto slajdu, ktorý určujú ďalšie elementy ako `title` alebo už samotný obsah.
  * Keďže každý slajd je v samostatnom súbore, bolo potrebné využiť nejakú navigáciu. Zvolil som ikony (šípky) z externáho zdroja `fontawesome` a pridal som ich vedľa slajdov (šípka vľavo = predchádzajúci slajd, šípka vpravo = nasledujúci slajd).

    Ukážka štruktúry tohto súboru:
    {% highlight xsl %}
<xsl:template match="slide[@type='full_screen']">
<div style="text-align:left;">
	<xsl:call-template name="title"/>
	<xsl:apply-templates/>
</div>
</xsl:template>{% endhighlight %}

* XSLT pre konverziu prezentácie XML -> PDF
  * Podobne ako XSLT pre HTML, aj pre PDF platia rovnaké podmienky ohľadom dodržiavania štruktúry `ppt.xml`.
