> Machine-translated from [README.md](README.md) into Français — corrections welcome.

# LamaVibe

<div align="center">
  <img src="packages/desktop/build/README-images/LamaVibe_ru.png" alt="Capture d'écran de LamaVibe" width="auto" />
</div>

<p align="center">
  <a href="https://deepvibe.eu/lamavibe">lamavibe.eu</a>
</p>

LamaVibe est la **version Ollama** de la famille _Vibe_ — un fork de ZCode centré sur un seul fournisseur : **Ollama** (modèles locaux). Un modèle, un espace de travail, un partenaire — pas un agent.

La famille _Vibe_ propose une application dédiée par fournisseur (DeepVibe pour DeepSeek, KimiVibe pour Kimi, LamaVibe pour Ollama, MiniVibe pour MiniMax, KlausVibe pour Claude, …), chacune avec son propre caractère. Elle existe **aux côtés** de ZCode, et non à sa place : ZCode pour le flux de travail multi-fournisseurs, les applications Vibe pour ceux qui veulent un modèle, un espace de travail, un partenaire. Consultez le dépôt source principal pour l'ensemble du code.

## Téléchargements

Les installateurs pour macOS, Windows et Linux sont publiés dans les [Releases](../../releases). Le programme de mise à jour intégré vérifie ce dépôt.

## Compilation depuis les sources

Nécessite Git, Node.js **24.14.0** et pnpm **10.33.2** (voir `mise.toml`).

```bash
pnpm bootstrap
# run the LamaVibe flavor in dev
pnpm dev:desktop:lama
# package (LamaVibe flavor)
ZCODE_LAMA_IDENTITY=1 pnpm bundle:desktop -- --os linux --arch x64
```

## Utilisation des modèles locaux

LamaVibe communique avec votre serveur [Ollama](https://ollama.com) local à l'adresse `http://localhost:11434/v1`. Le fournisseur intégré **Ollama (Local)** ne nécessite **aucune clé API**.

1. Assurez-vous qu'Ollama est en cours d'exécution et que vous disposez d'au moins un modèle de conversation, par exemple `ollama pull qwen2.5-coder:7b`.
2. Ouvrez **Paramètres → Fournisseurs de modèles → Ollama (Local) → Ajouter un modèle**.
3. Cliquez sur **Charger les modèles** pour lister les modèles installés sur votre machine et en choisir un (ou saisissez l'ID du modèle).
4. Conservez le format d'API sur **Compatible OpenAI (chat completions)**.

**Appels d'outils :** sous *Avancé → Capacités*, vous trouverez un interrupteur **Appels d'outils**. Il est **désactivé par défaut pour les fournisseurs locaux**, car la plupart des modèles locaux ne prennent pas en charge l'appel de fonctions ou l'exposent différemment. Ne l'activez que si votre modèle prend réellement en charge les appels d'outils Ollama — sinon Ollama rejette la requête avec l'erreur HTTP 400 `does not support tools`. Pour une simple conversation, laissez-le désactivé.

**Les modèles d'embedding** tels que `nomic-embed-*` sont destinés à la mémoire et à la recherche sémantique (embeddings), pas à la conversation — choisissez un modèle de conversation pour un fil.

## Licence et attribution

Basé sur ZCode (Apache-2.0) ; la licence et le NOTICE sont conservés. LamaVibe est un projet indépendant et n'est affilié ni à ZCode/Z.ai ni à Ollama. Ollama est une marque déposée de son propriétaire ; le logo est utilisé avec l'autorisation de l'exploitant.
