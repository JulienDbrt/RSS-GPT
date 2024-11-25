# RSS-GPT

## What is this?

[Configuration Guide](https://yinan-c.github.io/rss-gpt-manual-en.html)

Using GitHub Actions to run a simple Python script repeatedly: Calling OpenAI API to generate summaries for RSS feeds, and push the generated feeds to GitHub Pages. Easy to configure, no server needed.

### Features

- Use ChatGPT to summarize RSS feeds, and attach summaries to the original articles, support custom summary length and target language.
- Aggregate multiple RSS feeds into one, remove duplicate articles, subscribe with a single address.
- Add filters to your own personalized RSS feeds.
- Host your own RSS feeds on GitHub repo and GitHub Pages.

## Quick configuration guide

- Fork this repo
- Add Repository Secrets
    - U_NAME: your GitHub username
    - U_EMAIL: your GitHub email
    - WORK_TOKEN: your GitHub personal accesstoken with `repo` and `workflow` scope, get it from [GitHub settings](https://github.com/settings/tokens/new)
    - OPENAI_API_KEY(OPTIONAL, only needed when using AI summarization feature): Get it from [OpenAI website](https://platform.openai.com/account/api-keys)
- Enable GitHub Pages in repo settings, choose deploy from branch, and set the directory to `/docs`.
- Configure your RSS feeds in config.ini

You can check out [here](https://yinan-c.github.io/rss-gpt-manual-en.html) for a more detailed configuration guide.

## ChangeLog and updates

- As OpenAI released a new version of `openai` package on Nov 06, 2023.  [More powerful models are coming](https://openai.com/blog/new-models-and-developer-products-announced-at-devday), the way to call API also changed. As a result, the old script will no longer work with the latest version installed, and needs to be updated. Otherwise, you will have to set `openai==0.27.8` in `requirements.txt` to use the old version.
-  In the latest updates, **contexts longer than 16k tokens are no longer truncated, instead, will use the `gpt-4-1106-preview` model.** If you don't like this, let me know and I'll think about adding customizability to choose whether truncate or use `gpt-4-1106-preview` model.
- Check out the [CHANGELOG.md](CHANGELOG.md).

### Contributions are welcome!

- Feel free to submit issues and pull requests.

## Example feeds being processed

These feeds on hosted in the [`docs/` subdirectory](https://github.com/yinan-c/RSS-GPT/tree/main/docs) in this repo as well as on my [GitHub Pages](https://yinan-c.github.io/RSS-GPT/). Feel free to subscribe in your favorite RSS reader.

I will consider hosting more feeds in the future. Email me or submit an issue if there are any questions using the script or any suggestions.

- https://portail.basta.media/spip.php?page=backend&id_mot=163 -> https://JulienDbrt.github.io/RSS-GPT/Basta : médias libres : économie.xml
- https://feeds.feedburner.com/Bitcoin-Bingactualits -> https://JulienDbrt.github.io/RSS-GPT/Bing Actu : bitcoin.xml
- https://cryptotribune.fr/rss/category/Actualites-Bitcoin -> https://JulienDbrt.github.io/RSS-GPT/CryptoTribune : bitcoin.xml
- https://cryptotribune.fr/rss/category/Actualites-Crypto -> https://JulienDbrt.github.io/RSS-GPT/CryptoTribune : crypto.xml
- https://cryptotribune.fr/rss/category/Actualites-Finance -> https://JulienDbrt.github.io/RSS-GPT/CryptoTribune : finance.xml
- https://cryptotribune.fr/rss/category/actualites-marches -> https://JulienDbrt.github.io/RSS-GPT/CryptoTribune : marchés.xml
- https://cryptotribune.fr/rss/latest-posts -> https://JulienDbrt.github.io/RSS-GPT/CryptoTribune : tous les articles.xml
- https://emm.newsbrief.eu/rss/rss?language=fr&type=search&mode=advanced&atLeast=bitcoin -> https://JulienDbrt.github.io/RSS-GPT/EMM : bitcoin.xml
- https://flipboard.com/topic/fr-bitcoin.rss -> https://JulienDbrt.github.io/RSS-GPT/Flipboard : bitcoin.xml
- https://flipboard.com/topic/fr-consommation.rss -> https://JulienDbrt.github.io/RSS-GPT/Flipboard : consommation.xml
- https://flipboard.com/topic/fr-emploi.rss -> https://JulienDbrt.github.io/RSS-GPT/Flipboard : emploi.xml
- https://flipboard.com/topic/fr-immobilier.rss -> https://JulienDbrt.github.io/RSS-GPT/Flipboard : immobilier.xml
- https://flipboard.com/topic/fr-linky.rss -> https://JulienDbrt.github.io/RSS-GPT/Flipboard : linky.xml
- https://korben.info/feed -> https://JulienDbrt.github.io/RSS-GPT/Korben.xml
- https://www.lacryptomonnaie.net/feed/ -> https://JulienDbrt.github.io/RSS-GPT/La cryptomonnaie.xml
- https://nouvelles.droit.org/categs/rss/1003 -> https://JulienDbrt.github.io/RSS-GPT/Nouvelles Droits : consommation.xml
- https://nouvelles.droit.org/categs/rss/33 -> https://JulienDbrt.github.io/RSS-GPT/Nouvelles Droits : immobilier.xml
- http://flussi.annuda.saynete.net/corse_economie_rss.xml -> https://JulienDbrt.github.io/RSS-GPT/Saynète : Corse : économie.xml
- https://partner-feeds.20min.ch/rss/20minutes/economie -> https://JulienDbrt.github.io/RSS-GPT/20 minutes : CH : économie.xml
- https://www.20minutes.fr/feeds/rss-economie.xml -> https://JulienDbrt.github.io/RSS-GPT/20minutes : économie.xml
- https://www.7sur7.be/economie/rss.xml -> https://JulienDbrt.github.io/RSS-GPT/7sur7 : économie.xml
- https://www.7sur7.be/carriere/rss.xml -> https://JulienDbrt.github.io/RSS-GPT/7sur7 : carriere.xml
- https://www.bfmtv.com/rss/economie/ -> https://JulienDbrt.github.io/RSS-GPT/BFM : économie.xml
- https://www.bfmtv.com/rss/economie/international/ -> https://JulienDbrt.github.io/RSS-GPT/BFM : économie monde.xml
- https://www.bfmtv.com/rss/economie/economie-social/ -> https://JulienDbrt.github.io/RSS-GPT/BFM : économie sociale.xml
- https://www.bfmtv.com/rss/economie/entreprises/energie/ -> https://JulienDbrt.github.io/RSS-GPT/BFM : énergie.xml
- https://www.bfmtv.com/rss/economie/entreprises/aeronautique/ -> https://JulienDbrt.github.io/RSS-GPT/BFM : aéronautique.xml
- https://www.bfmtv.com/rss/auto/ -> https://JulienDbrt.github.io/RSS-GPT/BFM : auto.xml
- https://www.bfmtv.com/rss/economie/entreprises/assurance-banque/ -> https://JulienDbrt.github.io/RSS-GPT/BFM : banque.xml
- https://www.bfmtv.com/rss/economie/consommation/ -> https://JulienDbrt.github.io/RSS-GPT/BFM : consommation.xml
- https://www.bfmtv.com/rss/crypto/ -> https://JulienDbrt.github.io/RSS-GPT/BFM : crypto.xml
- https://www.bfmtv.com/rss/economie/emploi/ -> https://JulienDbrt.github.io/RSS-GPT/BFM : emploi.xml
- https://www.bfmtv.com/rss/economie/entreprises/ -> https://JulienDbrt.github.io/RSS-GPT/BFM : entreprise.xml
- https://www.bfmtv.com/rss/economie/entreprises/culture-loisirs/ -> https://JulienDbrt.github.io/RSS-GPT/BFM : entreprises loisirs.xml
- https://www.bfmtv.com/rss/economie/experts/ -> https://JulienDbrt.github.io/RSS-GPT/BFM : experts.xml
- https://www.bfmtv.com/rss/economie/economie-social/finances-publiques/ -> https://JulienDbrt.github.io/RSS-GPT/BFM : finances publiques.xml
- https://www.bfmtv.com/rss/tech/ -> https://JulienDbrt.github.io/RSS-GPT/BFM : high tech.xml
- https://www.bfmtv.com/rss/immobilier/ -> https://JulienDbrt.github.io/RSS-GPT/BFM : immobilier.xml
- https://www.bfmtv.com/rss/economie/patrimoine/impots-fiscalite/ -> https://JulienDbrt.github.io/RSS-GPT/BFM : impôts fiscalité.xml
- https://www.bfmtv.com/rss/economie/patrimoine/ -> https://JulienDbrt.github.io/RSS-GPT/BFM : patrimoine.xml
- https://www.bfmtv.com/rss/economie/patrimoine/immobilier/ -> https://JulienDbrt.github.io/RSS-GPT/BFM : patrimoine immobilier.xml
- https://www.bfmtv.com/rss/economie/patrimoine/placements-epargne/ -> https://JulienDbrt.github.io/RSS-GPT/BFM : placements épargne.xml
- https://www.bfmtv.com/rss/economie/patrimoine/retraite/ -> https://JulienDbrt.github.io/RSS-GPT/BFM : retraite.xml
- https://www.bfmtv.com/rss/economie/entreprises/services/ -> https://JulienDbrt.github.io/RSS-GPT/BFM : services.xml
- https://www.bfmtv.com/rss/economie/patrimoine/succession/ -> https://JulienDbrt.github.io/RSS-GPT/BFM : succession.xml
- https://feeds.simplecast.com/MdgHX7eu -> https://JulienDbrt.github.io/RSS-GPT/BFM : Tech and Co.xml
- https://www.bfmtv.com/rss/economie/entreprises/transports/ -> https://JulienDbrt.github.io/RSS-GPT/BFM : transports.xml
- https://www.bfmtv.com/rss/economie/emploi/vie-de-bureau/ -> https://JulienDbrt.github.io/RSS-GPT/BFM : vie de bureau.xml
- https://www.dna.fr/economie/rss -> https://JulienDbrt.github.io/RSS-GPT/Dernières Nouvelles d’Alsace : économie.xml
- https://www.dna.fr/magazine-immobilier/rss -> https://JulienDbrt.github.io/RSS-GPT/Dernières Nouvelles d’Alsace : immobilier.xml
- https://www.dna.fr/paroles-d-experts/rss -> https://JulienDbrt.github.io/RSS-GPT/Dernières Nouvelles d’Alsace : paroles d’experts.xml
- https://www.euractiv.fr/sections/economie/feed/ -> https://JulienDbrt.github.io/RSS-GPT/Euractiv : économie.xml
- https://www.euractiv.fr/sections/transport/feed/ -> https://JulienDbrt.github.io/RSS-GPT/Euractiv : transport.xml
- https://fr.euronews.com/rss?level=tag&name=cryptomonnaie -> https://JulienDbrt.github.io/RSS-GPT/Euronews FR : cryptomonnaie.xml
- https://www.europe1.fr/rss/economie.xml -> https://JulienDbrt.github.io/RSS-GPT/Europe 1 : économie.xml
- https://www.martinique.franceantilles.fr/actualite/economie/rss.xml -> https://JulienDbrt.github.io/RSS-GPT/France Antilles : Martinique : économie.xml
- https://www.francebleu.fr/theme/immobilier -> https://JulienDbrt.github.io/RSS-GPT/France Bleu : immobilier.xml
- https://www.francetvinfo.fr/economie.rss -> https://JulienDbrt.github.io/RSS-GPT/France Info : économie consommation.xml
- https://www.francetvinfo.fr/economie/aeronautique.rss -> https://JulienDbrt.github.io/RSS-GPT/France Info : aéronautique.xml
- https://www.francetvinfo.fr/economie/autoentrepreneurs.rss -> https://JulienDbrt.github.io/RSS-GPT/France Info : auto-entrepreneur.xml
- https://www.francetvinfo.fr/economie/bitcoin.rss -> https://JulienDbrt.github.io/RSS-GPT/France Info : bitcoin.xml
- https://www.francetvinfo.fr/economie/immobilier.rss -> https://JulienDbrt.github.io/RSS-GPT/France Info : immobilier.xml
- https://www.francetvinfo.fr/economie/transports.rss -> https://JulienDbrt.github.io/RSS-GPT/France Info : transports.xml
- https://www.radiofrance.fr/franceinter/rss/economie -> https://JulienDbrt.github.io/RSS-GPT/France Inter : économie.xml
- https://www.francesoir.fr/rss-tendance-eco.xml -> https://JulienDbrt.github.io/RSS-GPT/France Soir : tendance éco.xml
- https://www.moneyvox.fr/actu/rss.php -> https://JulienDbrt.github.io/RSS-GPT/MoneyVox.xml
- https://www.france24.com/fr/tag/cryptomonnaie/rss -> https://JulienDbrt.github.io/RSS-GPT/France24 : cryptomonnaie.xml
- https://france3-regions.francetvinfo.fr/environnement/energie/rss -> https://JulienDbrt.github.io/RSS-GPT/France3 : énergie.xml
- https://france3-regions.francetvinfo.fr/economie/rss?r=paris-ile-de-france -> https://JulienDbrt.github.io/RSS-GPT/France3 : Île-de-France : économie.xml
- https://france3-regions.francetvinfo.fr/economie/agriculture/rss -> https://JulienDbrt.github.io/RSS-GPT/France3 : agriculture.xml
- https://france3-regions.francetvinfo.fr/economie/rss?r=bourgogne-franche-comte -> https://JulienDbrt.github.io/RSS-GPT/France3 : Bourgogne-Franche-Comté : économie.xml
- https://france3-regions.francetvinfo.fr/economie/rss?r=bretagne -> https://JulienDbrt.github.io/RSS-GPT/France3 : Bretagne : économie.xml
- https://france3-regions.francetvinfo.fr/economie/emploi/rss -> https://JulienDbrt.github.io/RSS-GPT/France3 : emploi.xml
- https://france3-regions.francetvinfo.fr/economie/immobilier/rss -> https://JulienDbrt.github.io/RSS-GPT/France3 : immobilier.xml
- https://france3-regions.francetvinfo.fr/economie/transports/rss -> https://JulienDbrt.github.io/RSS-GPT/France3 : transports.xml
- https://www.journaldemontreal.com/actualite/consommation/rss.xml -> https://JulienDbrt.github.io/RSS-GPT/Journal de Montréal : consommation.xml
- https://www.journaldemontreal.com/actualite/transports/rss.xml -> https://JulienDbrt.github.io/RSS-GPT/Journal de Montréal : transports.xml
- https://lactualite.com/lactualite-affaires/feed/ -> https://JulienDbrt.github.io/RSS-GPT/L’actualité : affaires et économie.xml
- https://lactualite.com/dollars-et-cents/feed/ -> https://JulienDbrt.github.io/RSS-GPT/L’actualité : dollars et cents.xml
- https://www.lalsace.fr/magazine-automobile/rss -> https://JulienDbrt.github.io/RSS-GPT/L’Alsace : magazine automobile.xml
- https://www.lalsace.fr/magazine-immobilier/rss -> https://JulienDbrt.github.io/RSS-GPT/L’Alsace : magazine immobilier.xml
- https://partner-feeds.lessentiel.lu/rss/lessentiel-fr/economie -> https://JulienDbrt.github.io/RSS-GPT/L’Essentiel : économie.xml
- https://www.lexpress.fr/arc/outboundfeeds/rss/economie.xml -> https://JulienDbrt.github.io/RSS-GPT/L’Express : économie.xml
- https://www.lexpress.fr/arc/outboundfeeds/rss/entrepreneurs.xml -> https://JulienDbrt.github.io/RSS-GPT/L’Express : entrepreneurs.xml
- https://la1ere.francetvinfo.fr/economie/rss -> https://JulienDbrt.github.io/RSS-GPT/La 1ère : économie.xml
- https://la1ere.francetvinfo.fr/economie/rss?r=martinique -> https://JulienDbrt.github.io/RSS-GPT/La 1ère : Martinique : économie.xml
- https://la1ere.francetvinfo.fr/economie/transports/rss?r=martinique -> https://JulienDbrt.github.io/RSS-GPT/La 1ère : Martinique : transports.xml
- https://la1ere.francetvinfo.fr/economie/transports/rss -> https://JulienDbrt.github.io/RSS-GPT/La 1ère : transports.xml
- https://www.la-croix.com/RSS/UNIVERS_WECO -> https://JulienDbrt.github.io/RSS-GPT/La Croix : économie.xml
- https://www.la-croix.com/RSS/Economie/Economie-solidaire -> https://JulienDbrt.github.io/RSS-GPT/La Croix : économie solidaire.xml
- https://www.ladepeche.fr/economie/rss.xml -> https://JulienDbrt.github.io/RSS-GPT/La Dépêche : économie.xml
- https://www.ladepeche.fr/economie/emploi/rss.xml -> https://JulienDbrt.github.io/RSS-GPT/La Dépêche : emploi.xml
- https://www.ladepeche.fr/economie/immobilier/rss.xml -> https://JulienDbrt.github.io/RSS-GPT/La Dépêche : immobilier.xml
- https://www.dhnet.be/arc/outboundfeeds/rss/section/conso/travail/?outputType=xml -> https://JulienDbrt.github.io/RSS-GPT/La Dernière Heure : emploi.xml
- https://www.lalibre.be/arc/outboundfeeds/rss/section/economie/?outputType=xml -> https://JulienDbrt.github.io/RSS-GPT/La Libre Belgique : Belgique : économie.xml
- https://www.lalibre.be/arc/outboundfeeds/rss/section/belgique/mobilite/?outputType=xml -> https://JulienDbrt.github.io/RSS-GPT/La Libre Belgique : mobilité.xml
- https://www.latribune.fr/rss/rubriques/actualite.html -> https://JulienDbrt.github.io/RSS-GPT/La Tribune : économie.xml
- https://www.latribune.fr/rss/rubriques/ile-de-france.html -> https://JulienDbrt.github.io/RSS-GPT/La Tribune : Île-de-France.xml
- https://www.latribune.fr/feed.xml -> https://JulienDbrt.github.io/RSS-GPT/La Tribune : actualité.xml
