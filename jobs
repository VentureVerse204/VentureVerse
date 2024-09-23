import json

# Load the JSON file
with open('listings.json', 'r') as f:
    data = json.load(f)

# Open a markdown file to write the table
with open('jobs.md', 'w') as md_file:
    # Write table header
    md_file.write('| Company Name | Job Title | Location(s) | Apply Link |\n')
    md_file.write('|--------------|-----------|-------------|------------|\n')
    
    # Write each job as a table row
    for job in data:
        company_name = job['company_name']
        job_title = job['title'].replace('\u2013', '-')  # Fix for any special characters
        locations = ', '.join(job['locations'])
        apply_link = f"[Apply Here]({job['url']})"
        
        # Write the row
        md_file.write(f'| {company_name} | {job_title} | {locations} | {apply_link} |\n')
