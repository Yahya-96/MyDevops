

# Define source and backup directories
SOURCE_DIR="/home/kuzan"
BACKUP_DIR="/home/kuzan/backup"


# Check if the source directory exists
if [ ! -d "$SOURCE_DIR" ]; then
    echo "Error! Sorry, the source directory does not exist!"
    exit 1
fi

# Create the backup directory if it doesn't exist

if [ ! -d "$BACKUP_DIR" ]; then
    echo "Creating backup directory: $BACKUP_DIR"
    mkdir -p "$BACKUP_DIR"
fi


# Copy all .txt files from the source to the backup directory
cp "$SOURCE_DIR"/*.txt "$BACKUP_DIR" 2>/dev/null

# Check if any .txt files were copied
if [ $? -eq 0 ]; then
    echo "Great,the backup was successful!"
else
    echo "No .txt files found to copy."
fi

