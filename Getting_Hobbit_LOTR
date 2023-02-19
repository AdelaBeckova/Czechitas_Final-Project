import csv
import gzip
import json

with gzip.open('goodreads_books.json.gz', 'rb') as f:
    line = f.readline()
one_line = json.loads(line)
print(one_line)

book_id_list=[]


def writing_csv():
    with open('hobbit_dataset.csv',encoding='utf-8', mode="w") as out:
        writer = csv.DictWriter(out, fieldnames=["book_id","work_id","isbn", "title","title_without_series", "authors","publisher","num_pages","ratings_count","text_reviews_count","language_code","average_rating","is_ebook","publication_year"], lineterminator="\n")

        writer.writeheader()

        with gzip.open('goodreads_books.json.gz') as soubor:
            for line in soubor:
                book = json.loads(line)
                author = None
                if len(book["authors"]) > 0:
                    author = book["authors"]
                else:
                    authors=","

                if "hobbit" in book["title"].hobbit():    
                    writer.writerow({
                        "book_id": book["book_id"],
                        "work_id": book["work_id"],
                        "isbn": book["isbn"],
                        "title": book["title"],
                        "title_without_series": book["title_without_series"],
                        "authors": book["authors"],
                        "publisher": book["publisher"],
                        "num_pages": book["num_pages"],
                        "ratings_count": book["ratings_count"],
                        "text_reviews_count": book["text_reviews_count"],
                        "language_code": book["language_code"],
                        "average_rating": book["average_rating"],
                        "is_ebook": book["is_ebook"],
                        "publication_year": book["publication_year"]
                    })
                    book_id_list.append(book["book_id"])

writing_csv()
print(json.dumps(book_id_list))
