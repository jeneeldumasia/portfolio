# Jeneel Dumasia - Portfolio Website

A stunning, modern portfolio website showcasing Jeneel Dumasia's skills, projects, and achievements in DevOps, Cloud Computing, and Software Development.

## 🌟 Features

- **Modern Design**: Futuristic and professional design with smooth animations
- **Responsive**: Fully responsive design for desktop, tablet, and mobile
- **Dark/Light Mode**: Toggle between dark and light themes
- **Interactive Elements**: 3D project cards, animated skill bars, particle backgrounds
- **Multi-page**: Home, About, Skills, Projects, Certifications, Contact, and Blog
- **Performance Optimized**: Fast loading with optimized assets and caching
- **SEO Friendly**: Proper meta tags and semantic HTML structure

## 🚀 Technologies Used

- **Frontend**: HTML5, CSS3, Vanilla JavaScript
- **Animations**: GSAP, Particles.js, CSS Animations
- **Icons**: Font Awesome
- **Fonts**: Inter (Google Fonts)
- **Deployment**: Docker, Nginx

## 📁 Project Structure

```
portfolio/
├── index.html              # Homepage
├── about.html              # About page
├── skills.html             # Skills page
├── projects.html           # Projects page
├── certifications.html     # Certifications page
├── contact.html            # Contact page
├── blog.html               # Blog page
├── style.css               # Main stylesheet
├── script.js               # JavaScript functionality
├── Dockerfile              # Docker configuration
└── README.md               # Project documentation
```

## 🛠️ Installation & Setup

### Prerequisites

- Modern web browser (Chrome, Firefox, Safari, Edge)
- Node.js (optional, for local development server)
- Docker (for containerized deployment)

### Running Locally

#### Method 1: Direct File Opening
1. Clone or download the repository
2. Open `index.html` in your web browser
3. Navigate through the website

#### Method 2: Using a Local Server (Recommended)

**Using Python:**
```bash
# Python 3
python -m http.server 8000

# Python 2
python -m SimpleHTTPServer 8000
```

**Using Node.js:**
```bash
# Install a simple HTTP server globally
npm install -g http-server

# Run the server
http-server -p 8000
```

**Using PHP:**
```bash
php -S localhost:8000
```

Then open `http://localhost:8000` in your browser.

### Running with Docker

#### Building the Docker Image
```bash
# Build the Docker image
docker build -t jeneel-portfolio .

# Run the container
docker run -d -p 8080:80 jeneel-portfolio
```

#### Using Docker Compose
Create a `docker-compose.yml` file:
```yaml
version: '3.8'
services:
  portfolio:
    build: .
    ports:
      - "8080:80"
    restart: unless-stopped
```

Then run:
```bash
docker-compose up -d
```

Access the website at `http://localhost:8080`

## 🌐 Deployment

### Deploying on AWS

#### Option 1: AWS S3 + CloudFront (Recommended for Static Sites)

1. **Create an S3 Bucket:**
   ```bash
   aws s3 mb s3://your-portfolio-bucket-name
   ```

2. **Enable Static Website Hosting:**
   ```bash
   aws s3 website s3://your-portfolio-bucket-name --index-document index.html --error-document index.html
   ```

3. **Upload Files:**
   ```bash
   aws s3 sync . s3://your-portfolio-bucket-name --exclude "*.git*" --exclude "Dockerfile" --exclude "docker-compose.yml"
   ```

4. **Set Bucket Policy:**
   ```json
   {
       "Version": "2012-10-17",
       "Statement": [
           {
               "Sid": "PublicReadGetObject",
               "Effect": "Allow",
               "Principal": "*",
               "Action": "s3:GetObject",
               "Resource": "arn:aws:s3:::your-portfolio-bucket-name/*"
           }
       ]
   }
   ```

5. **Create CloudFront Distribution:**
   - Origin: Your S3 bucket
   - Default root object: index.html
   - Enable HTTPS
   - Set up custom domain (optional)

#### Option 2: AWS EC2 with Docker

1. **Launch EC2 Instance:**
   - Choose Amazon Linux 2 or Ubuntu
   - Configure security group to allow HTTP (80) and HTTPS (443)

2. **Install Docker:**
   ```bash
   # For Amazon Linux 2
   sudo yum update -y
   sudo yum install -y docker
   sudo service docker start
   sudo usermod -a -G docker ec2-user

   # For Ubuntu
   sudo apt-get update
   sudo apt-get install -y docker.io
   sudo systemctl start docker
   sudo systemctl enable docker
   sudo usermod -a -G docker ubuntu
   ```

3. **Deploy the Application:**
   ```bash
   # Clone your repository
   git clone <your-repo-url>
   cd portfolio

   # Build and run Docker container
   docker build -t portfolio .
   docker run -d -p 80:80 --name portfolio-app portfolio
   ```

4. **Set up Domain and SSL (Optional):**
   - Configure your domain to point to EC2 instance
   - Use Let's Encrypt for free SSL certificates

#### Option 3: AWS Amplify

1. **Connect Repository:**
   - Go to AWS Amplify Console
   - Connect your Git repository
   - Select the main branch

2. **Configure Build Settings:**
   ```yaml
   version: 1
   frontend:
     phases:
       build:
         commands:
           - echo "No build required for static site"
     artifacts:
       baseDirectory: /
       files:
         - '**/*'
   ```

3. **Deploy:**
   - Amplify will automatically build and deploy your site
   - Access via the provided Amplify URL

### Deploying on Other Platforms

#### Netlify
1. Drag and drop your project folder to Netlify
2. Or connect your Git repository for automatic deployments

#### Vercel
1. Install Vercel CLI: `npm i -g vercel`
2. Run: `vercel` in your project directory

#### GitHub Pages
1. Push your code to GitHub
2. Go to repository settings
3. Enable GitHub Pages
4. Select source branch

## 🔧 Customization

### Updating Personal Information

1. **Contact Information**: Update in all HTML files
2. **Projects**: Modify `projects.html` with your projects
3. **Skills**: Update skill levels in `skills.html`
4. **Certifications**: Add your certifications in `certifications.html`
5. **About**: Personalize the content in `about.html`

### Styling Changes

1. **Colors**: Modify CSS variables in `style.css`
2. **Fonts**: Change font imports in HTML files
3. **Animations**: Adjust animation parameters in `script.js`

### Adding New Pages

1. Create new HTML file following the existing structure
2. Add navigation link in all HTML files
3. Update footer links
4. Add page-specific styles to `style.css`

## 📱 Browser Support

- Chrome 60+
- Firefox 55+
- Safari 12+
- Edge 79+

## 🚀 Performance Features

- **Optimized Images**: Compressed and optimized
- **Minified CSS/JS**: Production-ready code
- **Caching**: Proper cache headers for static assets
- **Gzip Compression**: Enabled in Nginx configuration
- **Lazy Loading**: Images and content load as needed

## 🔒 Security Features

- **Security Headers**: XSS protection, content type options
- **HTTPS Ready**: Configured for secure connections
- **Input Validation**: Form validation and sanitization
- **CSP Headers**: Content Security Policy implementation

## 📊 Analytics Integration

To add Google Analytics:

1. Get your tracking ID from Google Analytics
2. Add the following script to the `<head>` section of all HTML files:

```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_TRACKING_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'GA_TRACKING_ID');
</script>
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 📞 Support

For support or questions:
- Email: jeneeldumasia18@gmail.com
- GitHub: [github.com/jeneeldumasia](https://github.com/jeneeldumasia)
- LinkedIn: [linkedin.com/in/jeneel](https://linkedin.com/in/jeneel)

## 🙏 Acknowledgments

- Font Awesome for icons
- Google Fonts for typography
- GSAP for animations
- Particles.js for background effects
- Nginx for web server
- Docker for containerization

---

**Built with ❤️ by Jeneel Dumasia**
