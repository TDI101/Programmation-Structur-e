Algorithme Gestion_ETUDIANT

    Structure Etudiant {
        Code : Entier
        Nom : Chaine de Charactères
        Age : Entier
        Note : Réel
    };
    
    Fonction trouveEtud_CODE(Code) : Entier {
        Début
            Pour i <- 1 à 100 faire
                Si (Te[i].Code == Code) faire
                    retourner i
                Fin Si
                i <- i + 1
            Fin Pour
            retourner -1
        Fin trouveEtud_CODE
    };
    
    Procedure AjoutEtud(ne) {
        Variables 
            Code : Entier
            Nom : Chaine de Charactères
            Age : Entier
            Note : Réel
            Statu : bool
        Début
            Ecrire('Entrez votre code : ');
            Lire(Code);
            Statu <- Vrai;
            TantQue (Statu) faire
                Si (trouveEtud_CODE(Code) == -1) alors
                    Te[ne].Code <- Code;
                    Ecrire('Entrez votre nom : ');
                    Lire(Nom);
                    TantQue (Statu) faire
                        Si (Nom != '') alors
                            Te[ne].Nom <- Nom;
                            Ecrire('Entrez votre age : ');
                            Lire(Age);
                            TantQue (Statu) faire
                                Si (Age > 0) alors
                                    Te[ne].Age <- Age;
                                    Ecrire('Entrez votre note : ');
                                    Lire(Note);
                                    TantQue (Statu) faire
                                        Si (Note >= 0) alors
                                            Te[ne].Note <- Note;
                                            Statu <- Faux;
                                        Sinon
                                            Ecrire('Votre note n\'est validé');
                                        Fin Si
                                    Fin TantQue
                                Sinon
                                    Ecrire('Votre age n\'est validé');
                                Fin Si
                            Fin TantQue
                        Sinon
                            Ecrire('Votre nom n\'est validé');
                        Fin Si
                    Fin TantQue
                Sinon
                    Ecrire('Votre code déja exist');
                Fin Si
            Fin TantQue
        Fin        
    };
    
    Procedure AfficheEtud(ne) {
        Début
            Pour i <- 1 à ne faire
                Ecrire('Etudiant [',i,']');
                Ecrire('>>> Code : ',Te[i].Code);
                Ecrire('>>> Nom : ',Te[i].Nom);
                Ecrire('>>> Age : ',Te[i].Age);
                Ecrire('>>> Note : ',Te[i].Note);
                i <- i + 1;
            Fin Pour
        Fin        
    };
    
    Procedure SupprimerEtud(cr, ne) {
        Variable ic : Entier
        Début
            ic <- trouveEtud_CODE(cr); /* Pour trouver l'index que se trouve le code */
            Si (ic > 0) alors
                Pour i <- 1 à ne faire
                    Si (i >= ic) alors
                        Si (i < ne) alors
                            Te[i] <- Te[i+1];
                        Sinon /* Pour Supprimer la répétition des information */
                            Te[i].Nom <- '';
                            Te[i].Code,Te[i].Age,Te[i].Note <- -1;
                        Fin Si
                    Fin Si
                    i <- i + 1;
                Fin Pour
            Sinon
                Ecrire('Votre code de recherche non trouvé dans la list des etudian');
            Fin Si
        Fin        
    };
    
    Procedure AfficheEtud_Sup_AGE(rsa, ne) {
        Début
            net <- 0;
            Pour i <- 1 à ne faire
                Si (Te[i].Age >= rsa) alors
                    net <- net + 1;
                    Ecrire('Etudiant [',i,']');
                    Ecrire('>>> Code : ',Te[i].Code);
                    Ecrire('>>> Nom : ',Te[i].Nom);
                    Ecrire('>>> Age : ',Te[i].Age);
                    Ecrire('>>> Note : ',Te[i].Note);
                Fin Si
                i <- i + 1
            Fin Pour
            Si (net == 0) alors
                Ecrire(net,' Etudiant trouvé');
            Fin Si
        Fin        
    };
    
    Procedure RechercheEtud_NOM(ne) {
        Variable npr : Chaine de Charactères
        Début
            net <- 0;
            Ecrire('Entrez une nom pour rechercher');
            Lire(npr);
            Si (npr != '') alors
                Pour i <- 1 à ne faire
                    Si (Te[i].Nom == npr) alors
                        net <- net + 1;
                        Ecrire('Etudiant [',i,']');
                        Ecrire('>>> Code : ',Te[i].Code);
                        Ecrire('>>> Nom : ',Te[i].Nom);
                        Ecrire('>>> Age : ',Te[i].Age);
                        Ecrire('>>> Note : ',Te[i].Note);
                    Fin Si
                    i <- i + 1;
                Fin Pour
                Si (net == 0) alors
                    Ecrire(net,' Etudiant trouvé');
                Fin Si
            Sinon
                Ecrire('Le nom pas validé');
            Fin Si
        Fin
    };
    
    Procedure RechercheEtud_CODE(ne) {
        Variable cpr : Entier
        Début
            net <- 0;
            Ecrire('Entrez une code pour rechercher');
            Lire(cpr);
            Pour i <- 1 à ne faire
                Si (Te[i].Code == cpr) alors
                    net <- net + 1;
                    Ecrire('Etudiant [',i,']');
                    Ecrire('>>> Code : ',Te[i].Code);
                    Ecrire('>>> Nom : ',Te[i].Nom);
                    Ecrire('>>> Age : ',Te[i].Age);
                    Ecrire('>>> Note : ',Te[i].Note);
                Fin Si
                i <- i + 1;
            Fin Pour
            Si (net == 0) alors
                Ecrire(net,' Etudiant trouvé');
            Fin Si
        Fin
    };
    
    Procedure RechercheEtud_AGE(apr,ne) {
        Début
            net <- 0;
            Pour i <- 1 à ne faire
                Si (Te[i].Age == apr) alors
                    net <- net + 1;
                    Ecrire('Etudiant [',i,']');
                    Ecrire('>>> Code : ',Te[i].Code);
                    Ecrire('>>> Nom : ',Te[i].Nom);
                    Ecrire('>>> Age : ',Te[i].Age);
                    Ecrire('>>> Note : ',Te[i].Note);
                Fin Si
                i <- i + 1;
            Fin Pour
            Si (net == 0) alors
                Ecrire(net,' Etudiant trouvé');
            Fin Si
        Fin
    };
    
    Procedur Affichemenu() {
        Variables le_choix, nae, cr, rsa, apr : Entier
        Début
            TantQue le_choix != 12 faire
                Ecrire('------MENU------------');
                Ecrire('1-Ajouter Etudiant');
                Ecrire('2-Supprimer Etudiant');
                Ecrire('3-AfficheR Etudiant');
                Ecrire('4-AfficheR LED Etudiant SUPERIEUR A UN AGE');
                Ecrire('5-Recherche Etudiant par nom');
                Ecrire('6-Recherche Etudiant par code');
                Ecrire('7-Recherche Etudiant par age');
                Ecrire('12-exit');
                Lire(le_choix);
                Selon Cas (le_choix) faire
                    Cas 1 :
                        Ecrire('Entrez number des etudiant pour ajouter');
                        Lire(nae);
                        Si (nae > 0 et (ne+nae) <= 100) alors
                            Pour i <- 1 à nae faire
                                ne <- ne + 1;
                                i <- i + 1;
                                AjoutEtud(ne);
                            Fin Pour
                        Sinon
                            Ecrire('Votre number des etudiant n\'est pas correct');
                        Fin Si
                    Cas 2 :
                        Si (ne > 0) alors
                            AfficheEtud(ne);
                        Sinon
                            Ecrire('N\'est pas dés etudiant trouvé');
                        Fin Si
                    Cas 3 :
                        Ecrire('Entrez le code pour rechercher');
                        Lire(cr);
                        Si (ne > 0) alors
                            SupprimerEtud(cr,ne);
                        Sinon
                            Ecrire('N\'est pas dés etudiant trouvé');
                        Fin Si
                    Cas 4 :
                        Ecrire('Entrez l\'age');
                        Lire(rsa);
                        Si (ne > 0) alors
                            AfficheEtud_Sup_AGE(rsa,ne);
                        Sinon
                            Ecrire('N\'est pas dés etudiant trouvé');
                        Fin Si
                    Cas 5 :
                        Si (ne > 0) alors
                            RechercheEtud_NOM(ne);
                        Sinon
                            Ecrire('N\'est pas dés etudiant trouvé');
                        Fin Si
                    Cas 6 :
                        Si (ne > 0) alors
                            RechercheEtud_CODE(ne);
                        Sinon
                            Ecrire('N\'est pas dés etudiant trouvé');
                        Fin Si
                    Cas 7 :
                        Ecrire('Entrez une age pour rechercher');
                        Lire(apr);
                        Si (ne > 0) alors
                            RechercheEtud_AGE(apr,ne);
                        Sinon
                            Ecrire('N\'est pas dés etudiant trouvé');
                        Fin Si
                    Sinon cas
                        Si (le_choix != 12) alors
                            Ecrire('Le choix pas correct');
                        Fin Si
                Fin selon
            Fin TantQue
        Fin
    };
        
    Tableau Te[100] : Etudiant
    Variables i, ne : Entier
    Début
        ne <- 0;
        Affichemenu();
    Fin
