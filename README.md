Ma libft, complétée au fur et à mesure.

# Contenu actuel
- libft de base
- is_in_set()
- ft_printf()
- get_next_line() version bonus (peut gérer plusieurs fichiers en même temps)

# Utiliser la libft dans un projet qui l'autorise
1. Clôner le dépôt à la racine du projet, enlever le .git.
2. Adapter le Makefile du projet:
   - assigner le chemin de l'archive à une nouvelle variable ``LIBFT_A := ./libft/libft``
   - ajouter les includes de la libft (libft.h) aux includes du projet: dans les CFLAGS ou une variable INCLUDES, ajouter `` -I ./libft/inc``
   - ajouter le chemin de l'archive (libft.a) dans les dépendances de $(NAME) et dans la règle de compilation
     ```
     $(NAME): $(OBJ) $(LIBFT_A)
       @${CC} ${CFLAGS} ${OBJ} $(LIBFT_A) -o $(NAME)
     ```
   - creer une règle pour l'archive afin qu'elle soit compilée à part du projet:
     ```
     $(LIBFT_A):
       @${MAKE} -C libft
     ```
   - sans oublier sa propre ligne dans le clean pour qu'elle soit nettoyée à part du projet:
     ```
     clean:
       @${MAKE} -C libft fclean
     ```
Et voilà! 
