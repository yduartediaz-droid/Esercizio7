-- Studenti
CREATE TABLE studenti (
    id_studente INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    data_iscrizione DATE NOT NULL
);

-- Corsi
CREATE TABLE corsi (
    id_corso INT PRIMARY KEY AUTO_INCREMENT,
    titolo VARCHAR(100) NOT NULL,
    descrizione TEXT,
    docente VARCHAR(100) NOT NULL
);

-- Iscrizioni
CREATE TABLE iscrizioni (
    id_iscrizione INT PRIMARY KEY AUTO_INCREMENT,
    id_studente INT NOT NULL,
    id_corso INT NOT NULL,
    data_iscrizione DATE NOT NULL,
    FOREIGN KEY (id_studente) REFERENCES studenti(id_studente),
    FOREIGN KEY (id_corso) REFERENCES corsi(id_corso)
);

-- Valutazioni
CREATE TABLE valutazioni (
    id_valutazione INT PRIMARY KEY AUTO_INCREMENT,
    id_iscrizione INT UNIQUE,
    voto DECIMAL(4,2),
    FOREIGN KEY (id_iscrizione) REFERENCES iscrizioni(id_iscrizione)
);