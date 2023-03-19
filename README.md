# projet-scala Groupe 4

## Participants : 
  - Téo Lambert
  - Malo Miquel
  - Clément Machado

## Instructions pour lancer le projet

### Prérequis

  * Java 8
  * SBT
  * Scala 2.12.4

### Lancement
Dans la console :
  
    * `scalac Main.scala` pour compiler le projet
    * `scala Main` pour lancer le projet

## Description du projet

### Liste des différentes actions implémentées:

#### Class `Main` 

La classe `Main` est la classe principale de l'application, qui contient la boucle principale du programme.

#### Companion obect `Pixel`

La classe `Pixel` est une classe qui représente un pixel dans un canvas, avec sa position et sa couleur.

  * `apply`: Méthode permettant de créer un pixel. Elle prend en entrée un entier correspondant à la position du pixel, et un entier correspondant à la couleur du pixel. Elle retourne un objet de type Pixel.

#### Class `Canvas`

La classe `Canvas` représente un canvas sur lequel des pixels peuvent être dessinés.

  * `display`: Méthode permettant d'afficher le contenu du canvas dans la console. Elle ne prend aucun argument en entrée.

  * `update`: Méthode permettant d'ajouter un pixel au canvas. Elle prend en entrée un objet de type Pixel, qui contient les informations sur la position et la couleur du pixel à ajouter. La méthode retourne un nouveau canvas contenant le pixel ajouté.

  * `updates`: Méthode permettant de mettre à jour plusieurs pixels en une seule fois. Elle prend en entrée une séquence de pixels de type Seq[Pixel], et applique la méthode update pour chaque pixel de la séquence. La méthode retourne un nouveau canvas contenant les pixels mis à jour.

#### Object `Canvas`

L'object `Canvas` contient des méthodes permettant de créer un canvas.

  * `createCanvas`: La méthode vérifie si les arguments passés sont valides pour créer un nouveau canvas. Si les arguments ne sont pas valides, un message d'erreur est renvoyé. Sinon, la méthode crée un nouveau canvas avec les dimensions passées en argument et l'initialise avec le caractère spécifié, puis renvoie le nouveau canvas avec un message de confirmation. Les arguments attendus sont une séquence de trois chaînes de caractères : la largeur du canvas, la hauteur du canvas et le caractère avec lequel initialiser le canvas.

  * `loadImage`: La méthode vérifie si un argument est passé pour la commande "load_image". Si aucun argument n'est passé, la méthode renvoie un message d'erreur. Sinon, la méthode tente de charger le fichier d'image dont le nom est spécifié dans le premier argument. Si le fichier est trouvé, la méthode crée un nouveau canvas avec les dimensions de l'image et l'initialise avec les pixels de l'image. Enfin, la méthode renvoie le nouveau canvas avec un message de confirmation. Les arguments attendus sont une séquence d'une chaîne de caractères : le nom du fichier d'image à charger.

  * `updatePixel`: La méthode vérifie si les arguments passés sont valides pour mettre à jour un pixel. Si les arguments ne sont pas valides, un message d'erreur est renvoyé. Sinon, la méthode crée un nouveau canvas mis à jour avec le pixel passé en argument et renvoie le nouveau canvas avec un message de confirmation. Les arguments attendus sont une séquence de trois chaînes de caractères : la coordonnée x du pixel à mettre à jour, la coordonnée y du pixel à mettre à jour et la nouvelle valeur du pixel. Les deux premiers arguments doivent être des entiers, le troisième argument doit être un caractère.

  * `draw`: La méthode vérifie si au moins deux arguments sont passés pour la commande "draw". Si moins de deux arguments sont passés, la méthode renvoie un message d'erreur. Sinon, la méthode détermine quelle commande de dessin a été demandée ("line", "rectangle", "triangle", "polygon", "fill") et appelle la fonction correspondante pour dessiner l'élément sur le canvas. Si la commande n'est pas reconnue, la méthode renvoie un message d'erreur. Les arguments attendus pour la commande "draw" dépendent de la commande de dessin spécifiée en premier argument. Par exemple, pour dessiner une ligne, les arguments attendus sont les coordonnées x et y des deux extrémités de la ligne, ainsi que le caractère utilisé pour dessiner la ligne. Pour dessiner un rectangle, les arguments attendus sont les coordonnées x et y du coin supérieur gauche du rectangle, sa largeur, sa hauteur et le caractère utilisé pour dessiner le rectangle. Les autres commandes de dessin ont également leurs propres arguments attendus.

  * `printCanvas`: La méthode prend un argument "canvas" de type Canvas et affiche le canvas à l'écran en affichant les caractères représentant les couleurs des pixels.

  * `drawLine`: La méthode vérifie si au moins quatre arguments sont passés pour la commande "line". Si moins de quatre arguments sont passés, la méthode renvoie un message d'erreur. Sinon, la méthode vérifie que les arguments sont valides : les coordonnées x et y de chaque pixel doivent être des entiers. Si les arguments ne sont pas valides, la méthode renvoie un message d'erreur.      Ensuite, la méthode extrait les coordonnées et la couleur des pixels à partir des arguments passés. Si les coordonnées sont en dehors du canvas, la méthode renvoie un message d'erreur. La méthode dessine ensuite la ligne sur le canvas, en utilisant la couleur spécifiée. Enfin, la méthode appelle la méthode "printCanvas" pour afficher le canvas avec la ligne dessinée, puis renvoie le nouveau canvas.

  * `drawRectangle`: La méthode vérifie si au moins quatre arguments sont passés pour la commande "rectangle". Si moins de quatre arguments sont passés, la méthode renvoie un message d'erreur. Sinon, la méthode vérifie que les arguments sont valides : les coordonnées x et y de chaque pixel doivent être des entiers. Si les arguments ne sont pas valides, la méthode renvoie un message d'erreur. Ensuite, la méthode extrait les coordonnées et la couleur des pixels à partir des arguments passés. La méthode utilise ces coordonnées pour dessiner les quatre lignes qui forment un rectangle en utilisant la méthode "drawLine". Enfin, la méthode renvoie le nouveau canvas.

  * `drawTriangle`: La méthode vérifie si au moins cinq arguments sont passés pour la commande "triangle". Si moins de cinq arguments sont passés, la méthode renvoie un message d'erreur. Sinon, la méthode vérifie que les arguments sont valides : les coordonnées x et y de chaque pixel doivent être des entiers. Si les arguments ne sont pas valides, la méthode renvoie un message d'erreur. Ensuite, la méthode extrait les coordonnées et la couleur des pixels à partir des arguments passés. La méthode utilise ces coordonnées pour dessiner les trois lignes qui forment un triangle en utilisant la méthode "drawLine". Enfin, la méthode renvoie le nouveau canvas.

  * `drawPolygon`: La méthode vérifie si au moins trois arguments sont passés pour la commande "polygon". Si moins de trois arguments sont passés, la méthode renvoie un message d'erreur. Sinon, la méthode vérifie que les arguments sont valides : les coordonnées x et y de chaque pixel doivent être des entiers. Si les arguments ne sont pas valides, la méthode renvoie un message d'erreur. Ensuite, la méthode extrait la couleur à partir du dernier argument passé. La méthode utilise cette couleur pour dessiner un polygone en utilisant l'algorithme de tracé de ligne de Bresenham dans la méthode "drawLine". Enfin, la méthode renvoie le nouveau canvas.

  * `fill`: Méthode permettant de remplir une forme avec une couleur donnée dans un canvas. Elle prend en argument une séquence de chaînes de caractères "arguments" et un objet "canvas" de type "Canvas".

  * `fillRecursive`: Méthode permettant de remplir récursivement une zone dans le canvas avec une couleur donnée. Elle prend en arguments les coordonnées (x, y) de départ, la couleur cible targetColor, la couleur de remplissage color, et le canvas sur lequel opérer.

## Répartitions des tâches:

Pour ce projet ci il n'y a pas eu réellement de répartition des tâches car nous nous sommes réunis et avons travaillé sur le même ordinateur tous ensemble. 