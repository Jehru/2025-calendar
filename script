const calendar = document.getElementById('calendar');
const daysLeftSpan = document.getElementById('daysLeftSpan');
const totalDays = 365; // Fixed number of days in 2025
const firstDayOfYear = new Date(2025, 0, 1); // January 1, 2025
const lastDayOfYear = new Date(2025, 11, 31); // December 31, 2025
const currentDate = new Date(); // Current date for comparison

// Generate dots for each day in 2025
for (let i = 0; i < totalDays; i++) {
    const dot = document.createElement('div');
    dot.classList.add('dot');

    // Calculate the date for this dot
    const thisDay = new Date(firstDayOfYear.getTime() + i * 24 * 60 * 60 * 1000);
    const formattedDate = thisDay.toLocaleDateString('en-GB', {
        weekday: 'long',
        day: '2-digit',
        month: '2-digit',
    });

    dot.setAttribute('data-date', formattedDate); // Tooltip for the date

    // Highlight the current day dynamically
    if (thisDay.toDateString() === currentDate.toDateString()) {
        dot.classList.add('current');
    }

    // Update days left and highlight previous dots on hover
    dot.addEventListener('mouseenter', () => {
        const daysLeft = totalDays - i; // Adjusted days left calculation
        daysLeftSpan.textContent = `${daysLeft}`;

        // Highlight all previous dots
        const allDots = document.querySelectorAll('.dot');
        allDots.forEach((d, index) => {
            if (index <= i) {
                d.style.backgroundColor = 'white';
            }
        });
    });

    // Reset dots and days left on mouse leave
    dot.addEventListener('mouseleave', () => {
        const allDots = document.querySelectorAll('.dot');
        allDots.forEach(d => {
            if (!d.classList.contains('current')) {
                d.style.backgroundColor = '#333';
            }
        });

        // Reset days left to default
        const defaultDaysLeft = totalDays - Math.floor((currentDate - firstDayOfYear) / (1000 * 60 * 60 * 24));
        daysLeftSpan.textContent = `${defaultDaysLeft}`;
    });

    calendar.appendChild(dot);
}

// Set initial days left
const initialDaysLeft = totalDays - Math.floor((currentDate - firstDayOfYear) / (1000 * 60 * 60 * 24));
daysLeftSpan.textContent = `${initialDaysLeft}`;