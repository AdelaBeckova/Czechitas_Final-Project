import csv
import json
import gzip

#hobbit_work_id="1540236"
#lotr_work_id="3462456"
#fellow_work_id="3204327"
#towers_work_id="2963845"
#king_work_id="2964424"
#lotr_hobbit_work_id="89369"

list_of_work_ids=["1540236","3462456","3204327","2963845","2964424","89369"]

book_id_list=[]

def writing_csv():
    with open('books_hobbit_lotr.csv',encoding='utf-8', mode="w") as out:
        with open('books_hobbit_lotr.json',encoding='utf-8', mode="w") as out_json:
            writer = csv.DictWriter(out, fieldnames=["book_id","work_id","isbn", "title","title_without_series", "authors","publisher","num_pages","ratings_count","text_reviews_count","language_code","average_rating","is_ebook","publication_year","publication_month"], lineterminator="\n")

            writer.writeheader()
            i=0
            with gzip.open('goodreads_books.json.gz') as soubor:
                for line in soubor:
                    book = json.loads(line)
                    author = None
                    if len(book["authors"]) > 0:
                        author = book["authors"]
                    else:
                        authors=","
                    i+=1
                    if i%100000==0:
                        print(i)
                    if book["work_id"] in list_of_work_ids:    
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
                            "publication_year": book["publication_year"],
                            "publication_month":book["publication_month"]
                        })
                        book_id_list.append(book["book_id"])
                        out_json.write(json.dumps(book)+"\n")

writing_csv()
