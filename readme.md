# Università

## Structure 

### Dipartimenti
- **ID** | INT - AUTO_INCREMENT - PK - UNIQUE - NOT NULL
- **Nome** | VARCHAR(200) - NOT NULL

### Corsi Laurea
- **ID** | INT - AUTO_INCREMENT - PK - UNIQUE - NOT NULL
- **Nome** | VARCHAR(200) - NOT NULL
- **Dipartimento_ID** | INT - FK - NOT NULL

### Corsi
- **ID** | INT - AUTO_INCREMENT - PK - UNIQUE - NOT NULL
- **Nome** | VARCHAR(200) - NOT NULL
- **Corso_Laurea_ID | INT - FK - NOT NULL

### Insegnanti
- **ID** | INT - AUTO_INCREMENT - PK - UNIQUE - NOT NULL
- **Nome_Cognome** | VARCHAR(200)
- **Corso_ID** | INT - FK

### Studenti
- **ID** | INT - AUTO_INCREMENT - PK - UNIQUE - NOT NULL
- **Nome_Cognome** | VARCHAR(200)
- **Corso_Laurea_ID** | INT - FK - NOT NULL

### Appelli
- **ID** | INT - AUTO_INCREMENT - PK - UNIQUE - NOT NULL
- **Data** | DATETIME
- **Corso_ID** | INT - FK
