<div align="center">

# SamuRecomp

**Samurai Shodown 64 (Samurai Spirits 64), reconstruit en programme natif.**<br>
Portage non officiel du jeu de combat d'arcade SNK de 1997 (Hyper Neo Geo 64), construit à partir des ROM que vous possédez.

[English](README.md) · [Guide de construction](docs/BUILD.md)

</div>

> [!IMPORTANT]
> SamuRecomp **ne contient pas le jeu** et n'en contiendra jamais. Il faut vos propres copies, obtenues légalement,
> de deux jeux de ROM d'arcade nommés comme dans MAME : `sams64.zip` (Samurai Shodown 64) et `hng64.zip` (les ROM
> système Hyper Neo Geo 64). La traduction du programme du jeu se fait **sur votre machine**. Ce dépôt ne contient que
> du code de projet et des outils libres. Ne publiez ni le programme compilé, ni `recomp/generated/`, ni `work/`,
> ni aucune ROM : ils sont fabriqués à partir du jeu de SNK (le `.gitignore` les exclut déjà).

## Ce que c'est

Pas un émulateur : le programme MIPS de l'arcade est traduit en C avec N64Recomp, puis compilé avec un modèle écrit
à la main du matériel Hyper Neo Geo 64 (vidéo, 3D, son, carte d'entrées/sorties). Même approche que
[ReBuriki](https://github.com/QuietClubGames/ReBuriki) pour Buriki One, dont ce projet est dérivé.

## État

Précoce mais jouable (testé avec Wine sur Steam Deck, en fenêtre et sans écran) : démarrage, logos, mode démo,
écran titre, pièce, start, choix du mode et du personnage, combats complets en couleurs (2D, 3D texturée, décors,
interface, combos), options d'affichage et de manette.

À vérifier ou à faire : le son (le processeur son tourne, mais il faut des écoutes), l'écran large et la 3D haute
définition (hérités de ReBuriki, non testés sur ce jeu), les options d'arcade (difficulté, free play, sang… :
il faut les adresses de la sauvegarde de ce jeu), l'installeur Windows `Setup.exe` (pas encore adapté).
Le jeu en ligne et « Unlock Silber » sont propres à Buriki One : désactivés (grisés).

Seul le jeu `sams64` (révision MAME) est géré pour l'instant.

## Construire

Voir **[docs/BUILD.md](docs/BUILD.md)**. En bref : extraire vos ROM avec `tools/sams64/unpack_roms_sams64.py`,
traduire avec `translate_sams64.py`, compiler avec `build_sams64_linux.py` (Linux, compilation croisée vers Windows,
testé sous Ubuntu 22.04), puis lancer avec Wine ou sous Windows.

## Touches par défaut

Joueur 1 : flèches, `Z X C V` = A B C D, `1` start, `5` pièce. Joueur 2 : `R F D G`, `A S Q W`, `2`, `6`.
`Échap` / `Tab` menu, `F11` plein écran, `F2` menu Test de l'arcade, `9` Service. Manettes de type Xbox prises en charge.

## Crédits et licences

ReBuriki (QuietClubGames, MIT), MAME (parties LGPL-2.1+/BSD-3-Clause), N64Recomp (MIT), ReLayer (MIT).
Voir [LICENSE.md](LICENSE.md). Projet non officiel, sans lien avec SNK.
