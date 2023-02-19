import json
import gzip

work_ids=['1540236', '3204327', '3462456', '2964424', '2963845'] # Hobbit:1540236 LotR1:3204327 LotR123:3462456 LotR3:2964424 LotR2:2963845
book_ids_to_work_ids = {}
i=0
count=0

with gzip.open('goodreads_books.json.gz','rt') as f:
    for line in f:
        #print('got line', line)
        item = json.loads(line)
        if item['work_id'] in work_ids:
            print('Found title: '+item['title']+' '+item['book_id'])
            book_ids_to_work_ids[item['book_id']]=item['work_id']
            count=count+1
        if i % 100000 == 0:
            print(i)
        i=i+1
print('items: '+str(i)+' found: '+str(count))
print(json.dumps(book_ids_to_work_ids))
