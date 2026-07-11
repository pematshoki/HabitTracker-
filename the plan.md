#Meme Trend Radar

Project Overview

Meme Trend Radar is a web-based dashboard designed to discover and visualize trending meme formats from Reddit communities in real time. The application uses an AI-powered web search to identify popular meme templates, analyze their popularity, and display them through an interactive radar interface and ranking board.

The dashboard presents meme trends in a visually appealing cyber-style interface with animated radar scanning, live status updates, and heat-based ranking.

Objective

The objective of the project is to:

Monitor current meme trends from Reddit.
Identify the most popular meme formats.
Rank meme templates based on popularity.
Display trends using an interactive dashboard.
Provide users with a quick overview of what's currently trending in meme communities.

System Workflow
User clicks "Scan Now"

        ↓

Application sends prompt to Claude API

        ↓

Claude performs web search on Reddit

        ↓

Trending meme formats are identified

        ↓

AI clusters similar meme formats

        ↓

Heat score is calculated

        ↓

Trend status is assigned
(Rising / Steady / Falling)

        ↓

Dashboard updates with latest trends

Features

1. Live Meme Trend Scanning

The application allows users to perform a live scan of current meme trends by clicking the Scan Now button.

During scanning:
Reads meme-related Reddit communities.
Searches for recent meme activity.
Groups similar meme formats.
Calculates popularity.

2. Interactive Radar Display

One of the main features is the animated radar visualization.

The radar:

Displays trending memes as radar blips.
Places hotter memes closer to the center.
Uses pulse animations.
Shows meme names when hovered.

The radar includes:
Rotating sweep animation
Signal indicators
Trend legend
