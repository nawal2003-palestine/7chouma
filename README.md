# 7chouma

# Structure du Site Web "7chouma" - Santé Sexuelle Éducative

## 🎯 Architecture Générale

### 1. PAGES PUBLIQUES (Sans connexion requise)
```
📁 Public/
├── index.php                    # Page d'accueil
├── about.php                    # À propos de 7chouma
├── resources.php                # Ressources éducatives publiques
├── contact.php                  # Contact et aide
└── privacy.php                  # Politique de confidentialité
```

### 2. SYSTÈME D'AUTHENTIFICATION
```
📁 Auth/
├── register.php                 # Inscription anonyme
├── login.php                    # Connexion
├── logout.php                   # Déconnexion
├── forgot-password.php          # Récupération mot de passe
└── verify-email.php             # Vérification email (optionnelle)
```

### 3. ESPACE UTILISATEUR PROTÉGÉ
```
📁 Dashboard/
├── dashboard.php                # Tableau de bord personnel
├── profile.php                  # Profil utilisateur (anonyme)
├── settings.php                 # Paramètres et langues
└── progress.php                 # Suivi des quiz et apprentissage
```

### 4. CONTENU ÉDUCATIF
```
📁 Education/
├── topics/
│   ├── contraception.php        # Méthodes contraceptives
│   ├── mst-ist.php             # Infections sexuellement transmissibles
│   ├── anatomie.php            # Anatomie et physiologie
│   ├── relations.php           # Relations saines
│   ├── consent.php             # Consentement
│   └── myths.php               # Mythes et réalités
├── articles/
│   ├── list.php                # Liste des articles
│   ├── article.php?id=x        # Article individuel
│   └── search.php              # Recherche d'articles
└── videos/
    ├── list.php                # Vidéos éducatives
    └── video.php?id=x          # Lecteur vidéo
```

### 5. OUTILS INTERACTIFS
```
📁 Tools/
├── quiz/
│   ├── list.php                # Liste des quiz
│   ├── quiz.php?id=x           # Quiz interactif
│   ├── results.php             # Résultats des quiz
│   └── stats.php               # Statistiques personnelles
├── scenarios/
│   ├── list.php                # Scénarios réels
│   ├── scenario.php?id=x       # Scénario interactif
│   └── feedback.php            # Retours sur scénarios
└── calculators/
    ├── cycle.php               # Calculateur de cycle
    ├── risk.php                # Évaluation des risques
    └── contraception.php       # Aide au choix contraceptif
```

### 6. FORUM COMMUNAUTAIRE
```
📁 Forum/
├── index.php                   # Accueil forum
├── categories.php              # Catégories de discussion
├── topic.php?id=x              # Sujet de discussion
├── post.php                    # Créer un nouveau sujet
├── reply.php                   # Répondre à un sujet
├── search.php                  # Recherche dans le forum
└── moderation/
    ├── reports.php             # Signalements
    └── moderate.php            # Interface de modération
```

### 7. SUPPORT ET AIDE
```
📁 Support/
├── help.php                    # Centre d'aide
├── faq.php                     # Questions fréquentes
├── emergency.php               # Contacts d'urgence
├── professionals.php           # Annuaire des professionnels
└── chat/
    ├── chat.php                # Chat avec modérateurs
    └── history.php             # Historique des conversations
```

## 🗂️ Structure Technique

### Base de Données MySQL
```sql
-- Utilisateurs (anonymes)
users (id, username, email_hash, password_hash, age_range, gender, created_at)

-- Contenu éducatif
articles (id, title_fr, title_ar, title_en, content_fr, content_ar, content_en, category, created_at)
videos (id, title, description, url, category, duration, created_at)
quiz (id, title, description, questions_json, category, difficulty, created_at)

-- Forum
forum_categories (id, name_fr, name_ar, name_en, description)
forum_topics (id, category_id, user_id, title, created_at, updated_at)
forum_posts (id, topic_id, user_id, content, created_at, is_moderated)

-- Suivi utilisateur
user_progress (id, user_id, quiz_id, score, completed_at)
user_bookmarks (id, user_id, content_type, content_id, created_at)
```

### Fichiers de Configuration
```
📁 Config/
├── database.php                # Configuration BDD
├── languages.php               # Gestion multilingue
├── security.php                # Paramètres sécurité
└── constants.php               # Constantes du site
```

### Composants Réutilisables
```
📁 Includes/
├── header.php                  # En-tête du site
├── footer.php                  # Pied de page
├── navigation.php              # Menu de navigation
├── sidebar.php                 # Barre latérale
├── auth-check.php              # Vérification connexion
└── functions.php               # Fonctions utilitaires
```

### Assets et Ressources
```
📁 Assets/
├── css/
│   ├── main.css                # Styles principaux
│   ├── responsive.css          # Styles responsive
│   └── themes/
│       ├── light.css           # Thème clair
│       └── dark.css            # Thème sombre
├── js/
│   ├── main.js                 # JavaScript principal
│   ├── quiz.js                 # Logique des quiz
│   ├── forum.js                # Interactions forum
│   └── chat.js                 # Système de chat
├── images/
│   ├── illustrations/          # Illustrations éducatives
│   ├── icons/                  # Icônes du site
│   └── avatars/                # Avatars anonymes
└── uploads/
    ├── documents/              # Documents téléchargés
    └── videos/                 # Vidéos uploadées
```

## 🔧 Fonctionnalités Clés à Développer

### Phase 1 - Core (Essential)
1. **Système d'inscription/connexion anonyme**
2. **Contenu éducatif de base** (articles + quiz)
3. **Interface multilingue** (FR/AR/EN)
4. **Forum de discussion modéré**
5. **Système de confidentialité robuste**

### Phase 2 - Avancé
1. **Chat en temps réel avec modérateurs**
2. **Outils interactifs** (calculateurs, scénarios)
3. **Système de gamification** (badges, points)
4. **API pour future app mobile**
5. **Analytics et statistiques d'usage**

### Phase 3 - Premium
1. **Consultations en ligne avec professionnels**
2. **Contenu personnalisé selon profil**
3. **Système de parrainage anonyme**
4. **Intégration avec services de santé locaux**

## 🚀 Prochaines Étapes Recommandées

1. **Commencer par la page d'accueil** (index.php)
2. **Créer le système d'authentification**
3. **Développer 2-3 articles éducatifs de base**
4. **Implémenter le forum simple**
5. **Tester avec un petit groupe d'utilisateurs**

Cette structure vous permet de démarrer progressivement et d'ajouter des fonctionnalités au fur et à mesure. Voulez-vous que je commence par créer la page d'accueil ou une autre partie spécifique ?
