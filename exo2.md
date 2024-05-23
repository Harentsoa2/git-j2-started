## Exercice 2 : Vues et index basiques
 #### Creer un index pour la table user
create index flash on "user"(first_name);
 
 #### Creer une vue pour la table user
create view user_public_data as
select first_name, last_name, email, âge, count(p.id_user) as nbr_post
from "user" u
INNER JOIN post p  on u.id_user = p.id_user
group by first_name, last_name, email, âge;


 #### Afficher la vue user_public_data
select * from user_public_data;

 #### Afficher les utilisateurs qui ont moins de 20 ans avec des postes
select * from user_public_data where age <= 20 and count(id_post) >= 1;


 #### Afficher la liste des utisateurs qui ont moins de 20 ans ayant déjà poster
 select last_name, first_name, count(id_post), from "user", post where age <= 20 and  count(id_post) >= 1;