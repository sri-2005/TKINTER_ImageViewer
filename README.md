# TKINTER_ImageViewer
Tkinter Image Viewer:** A Python-based GUI application using Tkinter and Pillow to browse and display images with a modern dark-themed according to my coustomization from scratch

📌 Features of Tkinter Image Viewer

✅ **Modern Dark-Themed UI** – A sleek **black-themed** interface with white text for a stylish, user-friendly experience.  

✅ **Full-Screen Mode** – Automatically launches in full-screen mode for an immersive image viewing experience.  

✅ **Image Navigation** – Easily navigate through images using **Next ⏩** and **Previous ⏪** buttons.  

✅ **Load Images from Folder** – Users can **open a folder** and browse images seamlessly.  

✅ **Default Image Display** – Shows **"SRI THARSHINI"** before any image is selected, making the UI more engaging.  

✅ **Error Handling** – Displays an error message if no images are found in the selected folder.  



📌 Step-by-Step Explanation

1️⃣ Importing Required Libraries 
   - Uses `tkinter` for GUI, `filedialog` to select folders, and `PIL` (Pillow) to handle image processing.  

2️⃣ Initializing the GUI Window
   - The app **opens in full-screen mode** with a **dark grayish-black background (`#1A1A1A`)**.  

3️⃣ Displaying Default Text Before Loading Images 
   - "SRI THARSHINI"** appears on the screen before selecting an image.  

4️⃣ Creating the Navigation Buttons
   - A **bottom frame** holds the navigation buttons, all styled with a **modern black theme and Times New Roman font**.  

5️⃣ Loading Images from a Folder  
   - The `load_images()` function lets users **select a folder** and **displays images automatically**.  

6️⃣ Displaying Images on Screen 
   - Images **resize dynamically** to fit the screen, ensuring smooth scaling.  

7️⃣ Navigating Between Images  
   - The **Next ⏩ and Previous ⏪** buttons cycle through the images in the selected folder.  

8️⃣ Running the Application
   - The app is started using `root.mainloop()`, which keeps the interface running.  

This Tkinter-based  Image Viewer is a simple yet powerful tool for **browsing images with a sleek UI. 🚀



import os
import tkinter as tk
from tkinter import filedialog
from PIL import Image, ImageTk

# initializing the GUI window
class ImageViewer:
    def __init__(self, root):
        self.root = root
        self.root.title("Image Viewer")
        self.root.attributes("-fullscreen", True)  # Set full screen mode
        self.root.configure(bg="#1A1A1A")  # Set a dark grayish black theme

        # display SRI THARSHINI before loading image
        self.image_label = tk.Label(self.root, text="SRI THARSHINI", font=("Times New Roman", 38, "bold italic"), fg="white", bg="#1A1A1A")
        self.image_label.pack(expand=True, fill=tk.BOTH)

        # creating the navigation buttons
        self.btn_frame = tk.Frame(self.root, bg="#1A1A1A")
        self.btn_frame.pack(fill=tk.X, side=tk.BOTTOM)

        # building a modernized navigation button for previous, next, open folder, exit
        self.prev_btn = tk.Button(self.btn_frame, text="⏪ Previous", command=self.prev_image, bg="black", fg="white", font=("Times New Roman", 16, "bold"), relief=tk.FLAT, padx=14, pady=8, borderwidth=2)
        self.prev_btn.pack(side=tk.LEFT, expand=True, padx=8, pady=8)
        
        self.next_btn = tk.Button(self.btn_frame, text="Next ⏩", command=self.next_image, bg="black", fg="white", font=("Times New Roman", 16, "bold"), relief=tk.FLAT, padx=14, pady=8, borderwidth=2)
        self.next_btn.pack(side=tk.LEFT, expand=True, padx=8, pady=8)
        
        self.open_btn = tk.Button(self.btn_frame, text="📂 Open Folder", command=self.load_images, bg="black", fg="white", font=("Times New Roman", 16, "bold"), relief=tk.FLAT, padx=14, pady=8, borderwidth=2)
        self.open_btn.pack(side=tk.LEFT, expand=True, padx=8, pady=8)
        
        self.exit_btn = tk.Button(self.btn_frame, text="❌ Exit", command=self.root.quit, bg="black", fg="white", font=("Times New Roman", 16, "bold"), relief=tk.FLAT, padx=14, pady=8, borderwidth=2)
        self.exit_btn.pack(side=tk.LEFT, expand=True, padx=8, pady=8)
        
        self.image_paths = []
        self.current_index = 0
        self.default_image_path = "default.png"  # Updated default image
        self.show_default_image()

    # display the default image before selection
    def show_default_image(self):
        if os.path.exists(self.default_image_path):
            try:
                image = Image.open(self.default_image_path)
                self.display_image(image)
            except Exception as e:
                print(f"Error loading default image: {e}")

    # loading and displaying images  
    def load_images(self):
        folder_path = filedialog.askdirectory()
        if folder_path:
            self.image_paths = [os.path.join(folder_path, f) for f in os.listdir(folder_path) 
                                if f.lower().endswith((".png", ".jpg", ".jpeg", ".bmp"))]
            if self.image_paths:
                self.current_index = 0
                self.show_image()
            else:
                tk.messagebox.showerror("Error", "No images found in the selected folder!")

    # displaying an image on screen
    def show_image(self):
        if self.image_paths:
            image = Image.open(self.image_paths[self.current_index])
            self.display_image(image)
    
    def display_image(self, image):
        screen_width = self.root.winfo_screenwidth()
        screen_height = self.root.winfo_screenheight() - 50  # Reduce height slightly to avoid taskbar blocking buttons
        image = image.resize((screen_width, screen_height))
        self.img = ImageTk.PhotoImage(image)
        self.image_label.config(image=self.img, text="", bg="#1A1A1A")  # Clear text when an image loads

    # navigation between images
    def next_image(self):
        if self.image_paths:
            self.current_index = (self.current_index + 1) % len(self.image_paths)
            self.show_image()
    
    def prev_image(self):
        if self.image_paths:
            self.current_index = (self.current_index - 1) % len(self.image_paths)
            self.show_image()

# run the application
if __name__ == "__main__":
    root = tk.Tk()
    app = ImageViewer(root)
    root.mainloop()


