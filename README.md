# Start the MySQL service
mysql-ctl start

# Log into the MySQL shell
mysql -u $C9_USER -p
mysql -u root -p

# Download the chinook database
wget https://raw.githubusercontent.com/lerocha/chinook-database/master/ChinookDatabase/DataSources/Chinook_MySql_AutoIncrementPKs.sql

# Import the Chinook SQL script file into MySQL
mysql -u $C9_USER -p < Chinook_MySql_AutoIncrementPKs.sql

# Open MySQL
mysql -u $C9_USER -p

# test.sql
test.sql script.
And it's a very simple script that counts the number of rows in the album and artist tables.

# Challenge 6
Find a playlist that contains only 1 track.

SELECT Playlist.Name as Playlist, COUNT(*) From Playlist 
INNER JOIN PlaylistTrack on Playlist.PlaylistId = PlaylistTrack.PlaylistId 

# Challenge 4
Create a query that shows our 10 biggest invoices by Total value, in descending order. If two invoices have the same Total, the more recent should appear first. The query should also show the Name of the Customer

SELECT 
    concat(Customer.FirstName, " ", Customer.LastName) as Name,
    Invoice.InvoiceDate as Date,
    Invoice.Total
FROM Invoice
INNER JOIN Customer ON Invoice.CustomerId = Customer.CustomerId
ORDER BY Total DESC, InvoiceDate DESC
LIMIT 10;
GROUP BY Playlist HAVING count(*) = 1;

# Challenge 3 
Create a list of the top 5 acts by number of tracks. The table should include the name of the artist and the number of tracks they have.
SELECT Artist.Name AS Artist, COUNT(Track.TrackId) AS Track FROM Artist
JOIN Album ON Artist.ArtistId = Album.ArtistId
JOIN Track ON Album.AlbumId = Track.AlbumId
GROUP BY Artist.Name
ORDER BY COUNT(Artist.Name)
DESC LIMIT 5;
