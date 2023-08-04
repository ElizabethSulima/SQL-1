CREATE TABLE genres (genre_id SERIAL PRIMARY KEY, id SERIAL, name VARCHAR(50) NOT NULL);

CREATE TABLE performers (performer_id SERIAL PRIMARY KEY, id SERIAL, name VARCHAR(50) NOT NULL);

CREATE TABLE albums (albums_id SERIAL PRIMARY KEY, id SERIAL, year_of_issue DATE NOT NULL);

CREATE TABLE track (track_id SERIAL PRIMARY KEY, id SERIAL, name VARCHAR(50) NOT NULL, duration NUMERIC, albums_id SERIAL NOT NULL, FOREIGN KEY (albums_id) REFERENCES albums(albums_id));

CREATE TABLE collection (collection_id SERIAL PRIMARY KEY, id SERIAL NOT NULL, name VARCHAR(50) NOT NULL, year_of_issue DATE NOT NULL);

CREATE TABLE genres_performers (gr_id SERIAL PRIMARY KEY, performer_id SERIAL, genre_id SERIAL, FOREIGN KEY (performer_id) REFERENCES performers(performer_id), FOREIGN KEY (genre_id) REFERENCES genres(genre_id));

CREATE TABLE albums_performers (ap_id SERIAL PRIMARY KEY, albums_id SERIAL, performer_id SERIAL, FOREIGN KEY (performer_id) REFERENCES performers(performer_id), FOREIGN KEY (albums_id) REFERENCES albums(albums_id));

CREATE TABLE track_collection (tc_id SERIAL PRIMARY KEY, track_id SERIAL, collection_id SERIAL, FOREIGN KEY (track_id) REFERENCES track(track_id), FOREIGN KEY (collection_id) REFERENCES collection(collection_id));