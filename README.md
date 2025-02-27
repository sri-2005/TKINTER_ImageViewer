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

