# <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MyFuture - Job Search and Upload</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&family=Roboto:wght@300;400&display=swap" rel="stylesheet">
    <style>
        /* Global Styles */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Poppins', sans-serif;
            background-color: #f4f9f9;
            color: #444;
            line-height: 1.6;
            padding: 0;
        }

        header {
            background: linear-gradient(135deg, #2F4F6A, #28a745);
            color: white;
            padding: 40px;
            text-align: center;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
        }

        header h1 {
            font-size: 3.5em;
            letter-spacing: 3px;
            font-weight: 600;
        }

        nav ul {
            list-style: none;
            text-align: center;
            margin-top: 20px;
        }

        nav ul li {
            display: inline-block;
            margin: 0 30px;
        }

        nav ul li a {
            color: #fff;
            font-size: 1.1em;
            font-weight: 400;
            text-decoration: none;
            transition: all 0.3s ease;
        }

        nav ul li a:hover {
            color: #28a745;
            text-decoration: underline;
        }

        .search-container, .upload-container {
            text-align: center;
            margin-top: 60px;
            padding: 40px 20px;
            background-color: #ffffff;
            box-shadow: 0 8px 40px rgba(0, 0, 0, 0.05);
            border-radius: 10px;
        }

        .search-container h2, .upload-container h2 {
            font-size: 2.8em;
            color: #2F4F6A;
            margin-bottom: 25px;
            font-weight: 600;
        }

        .search-container input[type="text"], .upload-container input[type="text"],
        .upload-container input[type="number"], .upload-container select,
        .upload-container textarea, .upload-container input[type="time"] {
            padding: 15px;
            font-size: 1.2em;
            width: 80%;
            margin-bottom: 20px;
            border-radius: 8px;
            border: 2px solid #ccc;
            transition: border 0.3s ease, box-shadow 0.3s ease;
        }

        .search-container input[type="text"]:focus, .upload-container input[type="text"]:focus,
        .upload-container input[type="number"]:focus, .upload-container select:focus,
        .upload-container textarea:focus, .upload-container input[type="time"]:focus {
            border-color: #28a745;
            outline: none;
            box-shadow: 0 0 8px rgba(40, 167, 69, 0.5);
        }

        .search-container button, .upload-container button {
            padding: 15px 30px;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 8px;
            font-size: 1.2em;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        .search-container button:hover, .upload-container button:hover {
            background-color: #218838;
        }

        .time-row {
            display: flex;
            justify-content: space-between;
            gap: 20px;
            margin-bottom: 20px;
        }

        .time-row input[type="time"] {
            width: 48%;
        }

        .about-section {
            text-align: center;
            margin-top: 60px;
            padding: 50px;
            background-color: #ffffff;
            box-shadow: 0 8px 40px rgba(0, 0, 0, 0.1);
            border-radius: 10px;
        }

        .about-section h2 {
            font-size: 2.5em;
            color: #2F4F6A;
            margin-bottom: 20px;
            font-weight: 600;
        }

        .about-section p {
            font-size: 1.3em;
            color: #555;
            line-height: 1.8;
            max-width: 800px;
            margin: 0 auto;
        }

        footer {
            background: #2F4F6A;
            color: white;
            text-align: center;
            padding: 30px 20px;
            margin-top: 60px;
            box-shadow: 0 -4px 15px rgba(0, 0, 0, 0.1);
        }

        footer p {
            font-weight: 300;
        }

        @media (max-width: 768px) {
            .search-container h2, .upload-container h2 {
                font-size: 2.2em;
            }

            .search-container input[type="text"], .upload-container input[type="text"],
            .upload-container input[type="number"], .upload-container select,
            .upload-container textarea {
                width: 90%;
            }

            .about-section p {
                font-size: 1.1em;
            }

            .time-row {
                flex-direction: column;
            }

            .time-row input[type="time"] {
                width: 100%;
                margin-bottom: 10px;
            }
        }
    </style>
</head>
<body>
    <header>
        <h1>MyFuture</h1>
        <nav>
            <ul>
                <li><a href="file:///C:/Users/msita/OneDrive/Documents/FBlAweb/homeapplicants.html">Home</a></li>
                <li><a href="file:///C:/Users/msita/OneDrive/Documents/FBlAweb/about.html">About</a></li>
                <li><a href="file:///C:/Users/msita/OneDrive/Documents/FBlAweb/contact.html">Contact</a></li>
                <li><a href="file:///C:/Users/msita/OneDrive/Documents/FBlAweb/login.html">Log In</a></li>
                <li><a href="file:///C:/Users/msita/OneDrive/Documents/FBlAweb/account.html">Create an Account</a></li>
            </ul>
        </nav>
    </header>

    <div class="search-container">
        <h2>Search for Jobs</h2>
        <input type="text" placeholder="Search for jobs by title or company" id="searchBar">
        <button onclick="searchJobs()">Search</button>

        <div id="dropdown" style="display:none;">
            <ul id="job-list">
                <!-- Job suggestions will appear here -->
            </ul>
        </div>
    </div>

    <div class="upload-container">
        <h2>Upload Job Listing</h2>
        <form>
            <input type="text" placeholder="Job Title" required>
            <input type="text" placeholder="Company Name" required>
            <input type="number" placeholder="Salary" required>
            <textarea placeholder="Job Description" rows="5" required></textarea>
            <select required>
                <option value="" disabled selected>Select Job Type</option>
                <option value="full_time">Full-Time</option>
                <option value="part_time">Part-Time</option>
                <option value="contract">Contract</option>
                <option value="internship">Internship</option>
            </select>
            <select required>
                <option value="" disabled selected>Select Work Location</option>
                <option value="virtual">Virtual</option>
                <option value="in_person">In-Person</option>
            </select>
            
            <div class="time-row">
                <input type="time" placeholder="Start Time" required>
                <input type="time" placeholder="End Time" required>
            </div>
            
            <button type="submit">Upload Job</button>
        </form>
    </div>

    <div class="about-section">
        <h2>About MyFuture</h2>
        <p>MyFuture connects talented individuals with top employers. Job seekers can search for opportunities, while employers can easily post job listings and find qualified candidates. Join us today and start building your future!</p>
    </div>

    <footer>
        <p>&copy; 2025 MyFuture | Empowering Employers & Job Seekers</p>
    </footer>

    <script>
        const jobOffers = [
            { title: 'Starbucks Barista', location: 'Duluth, GA', url: 'file:///C:/Users/msita/OneDrive/Documents/FBlAweb/starbucks.html' },
            { title: 'Software Engineer', location: 'Atlanta, GA', url: 'file:///C:/Users/msita/OneDrive/Documents/FBlAweb/engineer.html' },
            { title: 'Marketing Manager', location: 'New York, NY', url: 'file:///C:/Users/msita/OneDrive/Documents/FBlAweb/marketing.html' },
        ];

        document.getElementById('searchBar').addEventListener('input', function() {
            const query = this.value.toLowerCase();
            const filteredJobs = jobOffers.filter(job => job.title.toLowerCase().includes(query));
            
            const dropdown = document.getElementById('dropdown');
            const jobList = document.getElementById('job-list');
            
            jobList.innerHTML = ''; // Clear previous results
            if (filteredJobs.length > 0) {
                dropdown.style.display = 'block';
                filteredJobs.forEach(job => {
                    const li = document.createElement('li');
                    li.textContent = `${job.title} - ${job.location}`;
                    li.onclick = () => window.location.href = job.url;
                    jobList.appendChild(li);
                });
            } else {
                dropdown.style.display = 'none';
            }
        });
    </script>
</body>
</html>
