This program is a shellcode injector written in Rust. It downloads binary shellcode from an HTTP(S) server and injects it into a chosen process. The target process can be modified by editing the main.rs file.

The shellcode is encoded in Base64 using the encode.py script to ensure it can be downloaded and executed correctly. By default, the target process is explorer.exe, but you can change this by modifying the main.rs file.

I have had good results using shellcode generated with the Havoc C2 framework.
Steps to Use the Injector:

    Generate Shellcode:
        Use your preferred tool (e.g., Havoc C2 or any other shellcode generator) to generate the shellcode.

    Encode Shellcode:
        Use the provided encode.py script to Base64 encode the generated shellcode. This ensures that the shellcode can be safely transmitted over HTTP.

    Edit main.rs:
        Open the main.rs file and change the URL to point to the server hosting your Base64-encoded shellcode. Also, update the name or identifier of the shellcode if necessary.

    Run the Injector:
        After making the necessary changes, compile and run the injector. It will download the shellcode, decode it, and inject it into the specified target process (explorer.exe by default).

A lot of this code was written by Michael Taggart (https://github.com/mttaggart) in the project: https://github.com/mttaggart/rustyneedle
I created this Repo for my own storage of the code.

Encode shellcode: python3 ./encode.py ~/c2framework.bin 3 shellcode.txt
Compile exe: cargo build --target x86_64-pc-windows-gnu --release

