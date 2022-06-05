## Lab 6

In this lab we joined GitHub and worked through the Introduction to GitHub course, created a lab file, created and tested a Book class, created and tested a Library class, added books to the librarym, added ISBN, and a delete book method.

Technologies used for this lab:
- GitHub
- VSCode

The purpose of this lab was to learn about GitHub, to practice creating and testing classes, and to practice using methods.

```
class Book {
    constructor(title, author, pubDate, isbn) {
        this.title = title;
        this.author = author;
        this.pubDate = pubDate;
        this.isbn = isbn;
    }
}

//const atomicHabits = new Book("Atomic Habits", "James Clear", "10/16/2018");
//console.log(atomicHabits);

class Library {
    constructor(name) {
        this._name = name;
        this._books = [];
    }
    get books() {
       return JSON.parse(JSON.stringify(this._books));
    }
    get count() {
        return this._books.length;
    }
    addBook(book = {}) {
        const { title = "", author = "", pubDate = "", isbn = ""} = book;
        if(title.length > 0 && author.length > 0) {
            const newBook = { title, author, pubDate, isbn};
            this._books.push(newBook);
        }
    }
    listBooks() {
        for (const book of this._books) {
            const {title, author, pubDate, isbn} = book;
            console.log(`Title: ${title}, Author: ${author}, PubDate: ${pubDate}, ISBN: ${isbn}`);
        }
    }
    deleteBook(isbn) {
        for (const book of this._books) {
            for (let i=0; i < this._books.length; i++) {
                if(this._books[i].isbn == isbn) {
                    this._books.splice(i,i);
                }
            }
        }
    }
}

const library = new Library("New York Times Best Seller List");

const atomicHabits = new Book("Atomic Habits", "James Clear", "10/16/2018", "0735211299");
library.addBook(atomicHabits);


const thinkAgain = new Book("Think Again", "Adam Grant", "2/2/2021", "1984878107");
library.addBook(thinkAgain);

const callingBS = new Book("Calling Bullshit", "Carl Bergstrom & Jevin West", "8/4/2020", "0525509186");
library.addBook(callingBS);

const glassCastle = new Book("The Glass Castle", "Jeanette Walls", "3/1/2005", "074324754X");
library.addBook(glassCastle);

console.log(`Book Count: ${library.count}`);
library.listBooks();

console.log("* Library after delete *");
library.deleteBook("074324754X");
library.listBooks();
```
