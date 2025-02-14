## py-kms alternative front-end

### Backstory:
I came across a reddit post about it decided to test py-kms myself and to my suprise it is functional. however the webUI it provided lacks the design and burns my eyes out. so i decided to create this repository that holds Jinja2 template for py-kms. trust me pure HTML is not easy, hence i created this with comments to future me and to its contributors

### Features
- Clutterless Clients page
- Dark theme
- Modern CSS
- Dropdown Products page

### TODO
- when user clicks on the GLVK make it copy to clipboard

### Usage
locate templates directory of pykms and replace the content with whats in this project.

### Docker
I highly suggest using [11note](https://github.com/11notes/docker-kms)'s image. mount the template directory of this project to the container. example:

### Screenshots
![{81958E47-9251-4A4B-B0DF-9484DEFFCD50}](https://github.com/user-attachments/assets/d55efd2a-07ba-42be-ae8f-cbe5b996bd9a)

![{9E8E4E72-43B0-4FC3-9944-31E780FBCCF0}](https://github.com/user-attachments/assets/e3e9a34c-8fe9-4c5d-9509-749a057914ee)


```
name: "kms"
services:
  kms:
    image: "11notes/kms:465f4d1"
    container_name: "kms"
    environment:
      TZ: "Europe/Zurich"
    volumes:
      - "var:/kms/var"
    ports:
      - "1688:1688/tcp"
    restart: "always"
  kms-gui:
    image: "11notes/kms-gui:stable"
    container_name: "kms-gui"
    environment:
      TZ: "Europe/Zurich"
    volumes:
      - "var:/kms/var"
      - "/path/to/templates:/opt/py-kms/templates/"
    ports:
      - "8080:8080/tcp"
    restart: "always"
volumes:
  var:
```

# Libraries used
- [TailwindCSS](https://tailwindcss.com/)
- [jinja2](https://jinja.palletsprojects.com/)
