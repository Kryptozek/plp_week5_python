class Book:
    """A class representing a Book with various attributes and methods."""
    
    def __init__(self, title, author, pages, genre, published_year):
        """
        Initialize a new Book object.
        
        Args:
            title (str): The title of the book
            author (str): The author's name
            pages (int): Number of pages in the book
            genre (str): The book's genre
            published_year (int): Year the book was published
        """
        self.title = title
        self.author = author
        self.pages = pages
        self.genre = genre
        self.published_year = published_year
        self.current_page = 0
        self.bookmarked_pages = []
        
    def read(self, num_pages):
        """Read a specific number of pages and update current page."""
        if self.current_page + num_pages > self.pages:
            print(f"The book only has {self.pages} pages. You've reached the end!")
            self.current_page = self.pages
        else:
            self.current_page += num_pages
            print(f"You've read {num_pages} pages. Current page: {self.current_page}/{self.pages}")
    
    def bookmark(self):
        """Bookmark the current page."""
        self.bookmarked_pages.append(self.current_page)
        print(f"Page {self.current_page} has been bookmarked.")
    
    def go_to_page(self, page_number):
        """Jump to a specific page in the book."""
        if 0 <= page_number <= self.pages:
            self.current_page = page_number
            print(f"Moved to page {self.current_page}")
        else:
            print(f"Invalid page number. The book has {self.pages} pages.")
    
    def book_info(self):
        """Display information about the book."""
        return f"'{self.title}' by {self.author} ({self.published_year}) - {self.genre}, {self.pages} pages"


class Ebook(Book):
    """A class representing an electronic book, inheriting from Book."""
    
    def __init__(self, title, author, pages, genre, published_year, file_format, file_size):
        """
        Initialize a new Ebook object.
        
        Args:
            title (str): The title of the book
            author (str): The author's name
            pages (int): Number of pages in the book
            genre (str): The book's genre
            published_year (int): Year the book was published
            file_format (str): Format of the ebook (PDF, EPUB, etc.)
            file_size (float): Size of the file in MB
        """
        # Call the parent class constructor
        super().__init__(title, author, pages, genre, published_year)
        
        # Add Ebook-specific attributes
        self.file_format = file_format
        self.file_size = file_size
        self.device = None
        self.font_size = 12
        
    def read(self, num_pages):
        """Override the read method for Ebooks."""
        if self.device is None:
            print("Please set a device first to read this ebook.")
            return
        
        super().read(num_pages)
        print(f"Reading on {self.device} with font size {self.font_size}.")
    
    def set_device(self, device_name):
        """Set the device used to read the ebook."""
        self.device = device_name
        print(f"Ebook now set to be read on {self.device}")
    
    def change_font_size(self, new_size):
        """Change the font size for reading."""
        self.font_size = new_size
        print(f"Font size changed to {self.font_size}")
    
    def book_info(self):
        """Override book_info to include ebook-specific details."""
        base_info = super().book_info()
        return f"{base_info} - {self.file_format} format, {self.file_size}MB"


class AudioBook(Book):
    """A class representing an audio book, inheriting from Book."""
    
    def __init__(self, title, author, pages, genre, published_year, narrator, duration_hours):
        """
        Initialize a new AudioBook object.
        
        Args:
            title (str): The title of the book
            author (str): The author's name
            pages (int): Number of pages in the book
            genre (str): The book's genre
            published_year (int): Year the book was published
            narrator (str): The name of the narrator
            duration_hours (float): Total duration in hours
        """
        # Call the parent class constructor
        super().__init__(title, author, pages, genre, published_year)
        
        # Add AudioBook-specific attributes
        self.narrator = narrator
        self.duration_hours = duration_hours
        self.current_time = 0
        self.playback_speed = 1.0
    
    def read(self, hours):
        """Override the read method for AudioBooks to use time instead of pages."""
        if self.current_time + hours > self.duration_hours:
            print(f"The audiobook is only {self.duration_hours} hours long. You've reached the end!")
            self.current_time = self.duration_hours
        else:
            self.current_time += hours
            # Update current page based on percentage listened
            percentage_complete = self.current_time / self.duration_hours
            self.current_page = int(self.pages * percentage_complete)
            print(f"You've listened for {hours} hours. Current time: {self.current_time}/{self.duration_hours} hours")
            print(f"Equivalent page: {self.current_page}/{self.pages}")
    
    def set_playback_speed(self, speed):
        """Change the playback speed."""
        self.playback_speed = speed
        print(f"Playback speed set to {self.playback_speed}x")
    
    def book_info(self):
        """Override book_info to include audiobook-specific details."""
        base_info = super().book_info()
        return f"{base_info} - Narrated by {self.narrator}, {self.duration_hours} hours"


# Polymorphism Challenge - Vehicle Classes
class Vehicle:
    """Base class for all vehicles."""
    
    def __init__(self, make, model, year):
        """Initialize a vehicle with make, model and year."""
        self.make = make
        self.model = model
        self.year = year
    
    def move(self):
        """Generic movement method - will be overridden by child classes."""
        print("The vehicle moves.")
    
    def describe(self):
        """Return a description of the vehicle."""
        return f"{self.year} {self.make} {self.model}"


class Car(Vehicle):
    """A car class inheriting from Vehicle."""
    
    def __init__(self, make, model, year, fuel_type):
        """Initialize a car with additional fuel type attribute."""
        super().__init__(make, model, year)
        self.fuel_type = fuel_type
    
    def move(self):
        """Override the move method for Car."""
        print(f"The {self.describe()} drives on the road. 🚗")


class Plane(Vehicle):
    """A plane class inheriting from Vehicle."""
    
    def __init__(self, make, model, year, max_altitude):
        """Initialize a plane with additional max altitude attribute."""
        super().__init__(make, model, year)
        self.max_altitude = max_altitude
    
    def move(self):
        """Override the move method for Plane."""
        print(f"The {self.describe()} flies through the air at up to {self.max_altitude} feet. ✈️")


class Boat(Vehicle):
    """A boat class inheriting from Vehicle."""
    
    def __init__(self, make, model, year, hull_type):
        """Initialize a boat with additional hull type attribute."""
        super().__init__(make, model, year)
        self.hull_type = hull_type
    
    def move(self):
        """Override the move method for Boat."""
        print(f"The {self.describe()} sails across the water. 🚢")


# Demonstration of the classes and polymorphism
def demonstrate_book_classes():
    """Demonstrate the Book class hierarchy."""
    print("\n===== BOOK CLASS DEMONSTRATION =====")
    
    # Create a regular book
    novel = Book("The Great Gatsby", "F. Scott Fitzgerald", 180, "Classic", 1925)
    print(novel.book_info())
    novel.read(50)
    novel.bookmark()
    novel.read(30)
    
    # Create an ebook
    digital_book = Ebook("Python Crash Course", "Eric Matthes", 544, "Programming", 
                         2019, "PDF", 8.5)
    print(digital_book.book_info())
    digital_book.set_device("Kindle")
    digital_book.change_font_size(14)
    digital_book.read(100)
    
    # Create an audiobook
    audio_novel = AudioBook("Dune", "Frank Herbert", 412, "Science Fiction", 
                            1965, "Scott Brick", 21.5)
    print(audio_novel.book_info())
    audio_novel.set_playback_speed(1.5)
    audio_novel.read(3)


def demonstrate_polymorphism():
    """Demonstrate polymorphism with the Vehicle class hierarchy."""
    print("\n===== POLYMORPHISM DEMONSTRATION =====")
    
    # Create various vehicle objects
    sedan = Car("Toyota", "Camry", 2022, "Hybrid")
    jet = Plane("Boeing", "747", 2018, 35000)
    yacht = Boat("Sunseeker", "Predator", 2021, "Deep-V")
    
    # Create a list of vehicles to demonstrate polymorphism
    vehicles = [sedan, jet, yacht]
    
    # Polymorphically call move() on each vehicle
    for vehicle in vehicles:
        vehicle.move()


# Main function to run demonstrations
def main():
    print("🏗️ CLASS DESIGN AND POLYMORPHISM DEMONSTRATION 🎭\n")
    
    demonstrate_book_classes()
    demonstrate_polymorphism()
    
    print("\nAssignments completed successfully!")


if __name__ == "__main__":
    main()
