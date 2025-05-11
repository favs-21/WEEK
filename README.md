# WEEK
Question 1

    def display_info(self):
        print(f"\n[Computer]")
        print(f"Brand    : {self._brand}")
        print(f"Processor: {self._processor}")
        print(f"RAM      : {self._ram} GB")
        print(f"Storage  : {self._storage} GB")



    def display_info(self):
        super().display_info()
        print(f"Weight   : {self._weight} kg")



    def display_info(self):
        super().display_info()
        print(f"UPS      : {'Yes' if self._has_ups else 'No'}")



    try:
        with open(filename, "r") as infile:
            lines = infile.readlines()

        modified_lines = [modify_line(line) for line in lines]
        output_file = "modified_" + filename

        with open(output_file, "w") as outfile:
            outfile.writelines(modified_lines)

        print(f"File processed. Output saved to '{output_file}'.\n")

    except FileNotFoundError:
        print(f"Error: File '{filename}' not found.")
        return
    except PermissionError:
        print(f"Error: Permission denied for file '{filename}'.")
        return
    except Exception as e:
        print(f"Unexpected error: {e}")
        return

    # Create computer objects from file content (assumes correct format)
    devices = []
    for line in modified_lines:
        parts = line.strip().split(',')
        if parts[0] == "Laptop" and len(parts) == 6:
            # Format: Laptop,Brand,Processor,RAM,Storage,Weight
            devices.append(Laptop(parts[1], parts[2], int(parts[3]), int(parts[4]), float(parts[5])))
        elif parts[0] == "Desktop" and len(parts) == 6:
            # Format: Desktop,Brand,Processor,RAM,Storage,UPS(True/False)
            devices.append(Desktop(parts[1], parts[2], int(parts[3]), int(parts[4]), parts[5] == "TRUE"))

    # Display all devices (polymorphism)
    for device in devices:
        device.display_info()


if _name_ == "_main_":
    main()
    




    
