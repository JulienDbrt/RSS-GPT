# RSS-GPT

[![](https://img.shields.io/github/last-commit/yinan-c/RSS-GPT/main?label=feeds%20refreshed)](https://yinan-c.github.io/RSS-GPT/)
[![](https://img.shields.io/github/license/yinan-c/RSS-GPT)](https://github.com/yinan-c/RSS-GPT/blob/master/LICENSE)


## 这是什么？

[中文介绍](https://yinan-c.github.io/rss-gpt.html) | [中文教程](https://yinan-c.github.io/rss-gpt-manual-zh.html) | [README](README.md)

使用 GitHub workflow 自动运行一个简单的 Python 脚本，调用 OpenAI API 为 RSS 订阅源生成摘要，然后将新生成的 RSS 订阅源推送到 GitHub Pages。配置简单快速，无需服务器。

### 功能及示例

- 使用 ChatGPT 来总结 RSS 订阅源, 生成关键词，摘要附在原文前面，支持自定义摘要长度，自定义语言。
- 聚合多个 RSS 订阅源，去除重复文章，用单一地址订阅。
- 为 RSS 订阅源添加基于标题，内容，URL 的关键词过滤器。
- 在 GitHub 仓库和 GitHub Pages 上自托管 RSS 订阅源。

![](https://i.imgur.com/7darABv.jpg)

## 快速部署

- Fork 这个仓库中
- 添加仓库 Secrets
    - U_NAME: 你的 GitHub 用户名
    - U_EMAIL: 你的 GitHub 邮箱
    - WORK_TOKEN: 你的 GitHub 个人访问令牌, 需要有 `repo` 和 `workflow` 权限。在 [GitHub 设置](https://github.com/settings/tokens/new)获取
    - OPENAI_API_KEY(可不填, 只有在使用 AI 摘要功能时需要): 你的 OpenAI API 密钥, 在 [OPENAI 网站](https://platform.openai.com/account/api-keys)获取
- 在仓库设置中启用 GitHub Pages， 选择 deploy from branch，设置目录为 `/docs`.
- 在 `config.ini` 中配置你的RSS订阅源

也可以参考更详细的[中文教程](https://yinan-c.github.io/rss-gpt-manual-zh.html)。

## 脚本的更新

- 由于 OpenAI 在 2023-11-06 发布了新版本的 `openai` 包，[新版本包含了更强大的模型](https://openai.com/blog/new-models-and-developer-products-announced-at-devday)，调用 API 的方式也发生了变化。因此，旧版本的脚本将无法使用最新版本的 `openai` 包，需要更新。否则，你可以在 `requirements.txt` 中设置 `openai==0.27.8` 来使用旧版本。
- 在更新的版本中，**长度超过 16k 个 token 的文章不再被截断，而是使用最新的 `gpt-4-1106-preview` 模型。** 如果你不喜欢这样的改变，可以联系我，我会考虑添加自定义选项来选择是否截断或者使用 `gpt-4-1106-preview` 模型。

- 查看 [CHANGELOG-zh.md](CHANGELOG-zh.md) 获取其他最新的更新日志。

### 欢迎贡献!

- 欢迎提交 issue 和 pull request。

## 分享几条本项目处理后的 RSS 订阅源

我自己用此脚本总结的一些 RSS订阅源托管在本项目的[`docs/`子目录](https://github.com/yinan-c/RSS-GPT/tree/main/docs)中以及我的 [GitHub Pages](https://yinan-c.github.io/RSS-GPT/)上找到。欢迎在任何 RSS 阅读器中订阅。

如果有任何问题或有关于 RSS feeds 的建议，欢迎邮件联系我。

如果你觉得本项目有帮助，欢迎 star。也可以考虑捐赠以支持我继续维护本项目以及 cover OpenAI API 的支出。感谢支持。

<a href="https://www.buymeacoffee.com/yinan" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>

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
