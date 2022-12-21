
library = []


def insert_book(**kwargs):
    book = {
        'title': kwargs.get('title'),
        'author': kwargs['author'],
        'isbn': kwargs.get('isbn', '1111111'),
    }
    library.append(book)
    return (True, 'success added')


def show_specific_book(book):
    for key, value in book.items():
        print(f'{key} => {value}')


def show_books(library):
    for book in library:
        # print(book)
        """model aval"""
        # print('title is :' + book['title'])
        # print('isbn is :' + book['isbn'])
        """model dovom"""
        # for key, value in book.items():
        #     print(f'{key} => {value}')
        """model sevom"""
        show_specific_book(book)


def search_book(library, key, value):
    for book in library:
        if book[key] == value:
            return book
    return None


def modify_book(book, key, new_value):
    book[key] = new_value


def delete_book(library, book):
    library.remove(book)


while True:
    vorodi = input("""
    1 => insert book
    2 => show book
    3 => show specific book
    4 => modify book
    5 => delete book
    
    """)
    if vorodi == '1':
        print('***********insert book************')
        res = insert_book(title=input('title:\n'), author=input('author:\n'),
                          isbn=input('isbn:\n'))
        print(res)
    elif vorodi == '2':
        print('***********show book************')
        show_books(library)
    elif vorodi == '3':
        print('***********show specific book************')

        key = input('key for search')
        value = input('value for search')
        book = search_book(library, key, value)
        if book is None:
            print('Not exists')
            continue
        show_specific_book(book)
    elif vorodi == '4':
        print('***********modify specific book************')
        key = input('key for search: \n')
        value = input('value forcd  search: \n')
        book = search_book(library, key, value)
        if book is None:
            print('Not exists\n')
            continue
        key = input('key for modify: \n')
        value = input('value for modify: \n')
        modify_book(book, key, value)
    elif vorodi == '5':
        print('***********delete specific book************')

        key = input('key for search')
        value = input('value for search')
        book = search_book(library,key, value)
        if book is None:
            print('Not exists\n')
            continue
        delete_book(library, book)
