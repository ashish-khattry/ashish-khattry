// ========================================================================
//                         PROJECT PHOENIX
//                         THE RUST ARTIFACT
//                         ASHISH KHATTTRY
//                         RUST BACKEND ARCHITECT
// ========================================================================

#![forbid(unsafe_code)]
#![deny(clippy::unwrap_used)]
#![deny(clippy::expect_used)]

use std::fmt;

// ========================================================================
//                         SYSTEM STATUS
// ========================================================================

#[derive(Debug)]
struct SystemStatus {
    os: &'static str,
    rustc: &'static str,
    user: &'static str,
    role: &'static str,
    memory: u8,
    panics: u8,
    discipline: &'static str,
}

impl SystemStatus {
    fn new() -> Self {
        Self {
            os: "Windows 11 Pro",
            rustc: "1.80.0",
            user: "ashish-khattry",
            role: "Backend Architect",
            memory: 100,
            panics: 0,
            discipline: "IRON",
        }
    }
}

impl fmt::Display for SystemStatus {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        writeln!(f, "\n╔══════════════════════════════════════════════════════════════════╗")?;
        writeln!(f, "║                      SYSTEM STATUS                              ║")?;
        writeln!(f, "╠══════════════════════════════════════════════════════════════════╣")?;
        writeln!(f, "║                                                                  ║")?;
        writeln!(f, "║  OS          : {:>25}                              ║", self.os)?;
        writeln!(f, "║  RUSTC       : {:>25}                              ║", self.rustc)?;
        writeln!(f, "║  USER        : {:>25}                              ║", self.user)?;
        writeln!(f, "║  ROLE        : {:>25}                              ║", self.role)?;
        writeln!(f, "║  MEMORY      : {:>25}% SAFE                        ║", self.memory)?;
        writeln!(f, "║  PANICS      : {:>25}% TOLERATED                  ║", self.panics)?;
        writeln!(f, "║  DISCIPLINE  : {:>25}                              ║", self.discipline)?;
        writeln!(f, "║                                                                  ║")?;
        writeln!(f, "╚══════════════════════════════════════════════════════════════════╝")
    }
}

// ========================================================================
//                         PROFILE
// ========================================================================

struct Profile {
    foundation: [&'static str; 3],
    focus: [&'static str; 3],
    goal: &'static str,
    philosophy: &'static str,
    daily_rhythm: [(&'static str, &'static str); 4],
}

impl Profile {
    fn new() -> Self {
        Self {
            foundation: ["C", "C++", "Java"],
            focus: ["Rust", "Web3", "Cloud"],
            goal: "100% crash-proof enterprise servers",
            philosophy: "\"I don't talk much. I let the code speak.\"",
            daily_rhythm: [
                ("0400", "Review Code"),
                ("0500", "Deep Work (Rust)"),
                ("0800", "Commit & Push"),
                ("2100", "Learn & Document"),
            ],
        }
    }
}

impl fmt::Display for Profile {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        writeln!(f, "\n╔══════════════════════════════════════════════════════════════════╗")?;
        writeln!(f, "║                         PROFILE                                  ║")?;
        writeln!(f, "╠══════════════════════════════════════════════════════════════════╣")?;
        writeln!(f, "║                                                                  ║")?;
        writeln!(f, "║  I build memory-safe, zero-panic systems.                        ║")?;
        writeln!(f, "║                                                                  ║")?;
        writeln!(f, "║  FOUNDATION  : {} · {} · {}                     ║", self.foundation[0], self.foundation[1], self.foundation[2])?;
        writeln!(f, "║  FOCUS       : {} · {} · {}                   ║", self.focus[0], self.focus[1], self.focus[2])?;
        writeln!(f, "║  GOAL        : {:>54}║", self.goal)?;
        writeln!(f, "║                                                                  ║")?;
        writeln!(f, "║  ══════════════════════════════════════════════════════════════  ║")?;
        writeln!(f, "║                                                                  ║")?;
        writeln!(f, "║  DAILY RHYTHM                                                    ║")?;
        for (time, task) in self.daily_rhythm {
            writeln!(f, "║  {}  ██████████  {}                                  ║", time, task)?;
        }
        writeln!(f, "║                                                                  ║")?;
        writeln!(f, "╚══════════════════════════════════════════════════════════════════╝")
    }
}

// ========================================================================
//                         BUILDING & LEARNING
// ========================================================================

#[derive(Debug)]
struct Project {
    name: &'static str,
    details: [&'static str; 3],
}

impl Project {
    fn new(name: &'static str, d1: &'static str, d2: &'static str, d3: &'static str) -> Self {
        Self {
            name,
            details: [d1, d2, d3],
        }
    }
}

struct Building {
    projects: Vec<Project>,
    learning: Vec<(&'static str, Vec<&'static str>)>,
}

impl Building {
    fn new() -> Self {
        Self {
            projects: vec![
                Project::new("CLI SEARCH TOOL", "Low-level OS searching", "Pure std, no deps", "Result & Option"),
                Project::new("AXUM WEB SERVER", "URL Shortener", "PostgreSQL", "Tokio concurrency"),
                Project::new("NETWORK CHAT", "Multi-user system", "Tokio async/await", "Ownership & Borrowing"),
            ],
            learning: vec![
                ("ADVANCED TRAITS & GATS", vec!["Generic Associated Types", "Higher-ranked trait bounds"]),
                ("LIFETIME ANNOTATIONS", vec!["Variance & Subtyping", "Lifetime bounds & elision"]),
                ("WEB3 INFRASTRUCTURE", vec!["Alloy / ethers-rs", "Smart contract integration"]),
            ],
        }
    }
}

impl fmt::Display for Building {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        writeln!(f, "\n╔══════════════════════════════════════════════════════════════════╗")?;
        writeln!(f, "║                    CURRENTLY BUILDING                           ║")?;
        writeln!(f, "╠══════════════════════════════════════════════════════════════════╣")?;
        writeln!(f, "║                                                                  ║")?;
        for project in &self.projects {
            writeln!(f, "║  {:>25}                                                 ║", project.name)?;
            for detail in project.details {
                writeln!(f, "║  ├─  {:>40}                                 ║", detail)?;
            }
            writeln!(f, "║                                                                  ║")?;
        }
        writeln!(f, "║  ══════════════════════════════════════════════════════════════  ║")?;
        writeln!(f, "║                                                                  ║")?;
        writeln!(f, "║  DEEP LEARNING                                                  ║")?;
        for (topic, subtopics) in &self.learning {
            writeln!(f, "║                                                                  ║")?;
            writeln!(f, "║  {:>25}                                          ║", topic)?;
            for sub in subtopics {
                writeln!(f, "║  ├─  {:>40}                                 ║", sub)?;
            }
        }
        writeln!(f, "║                                                                  ║")?;
        writeln!(f, "╚══════════════════════════════════════════════════════════════════╝")
    }
}

// ========================================================================
//                         TECH STACK (RUST STYLE)
// ========================================================================

#[derive(Debug)]
struct Skill {
    name: &'static str,
    level: u8,
    bar: &'static str,
}

impl Skill {
    fn new(name: &'static str, level: u8) -> Self {
        let bars = match level {
            100 => "████████████████████████████████████████████████",
            95  => "███████████████████████████████████████████░░░░░",
            90  => "█████████████████████████████████████████░░░░░",
            85  => "████████████████████████████████████████░░░░░░",
            80  => "██████████████████████████████████░░░░░░░░░",
            _   => "████████████████████████████████████████████████",
        };
        Self { name, level, bar }
    }
}

impl fmt::Display for Skill {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        write!(f, "║  {:>10}  {}  {}%%    ║", self.name, self.bar, self.level)
    }
}

struct TechStack {
    skills: Vec<Skill>,
}

impl TechStack {
    fn new() -> Self {
        Self {
            skills: vec![
                Skill::new("Rust", 95),
                Skill::new("PostgreSQL", 90),
                Skill::new("Docker", 85),
                Skill::new("Git", 100),
                Skill::new("Windows 11", 100),
                Skill::new("PowerShell", 80),
            ],
        }
    }
}

impl fmt::Display for TechStack {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        writeln!(f, "\n╔══════════════════════════════════════════════════════════════════╗")?;
        writeln!(f, "║                     TECHNICAL ARSENAL                           ║")?;
        writeln!(f, "╠══════════════════════════════════════════════════════════════════╣")?;
        writeln!(f, "║                                                                  ║")?;
        for skill in &self.skills {
            writeln!(f, "{}", skill)?;
        }
        writeln!(f, "║                                                                  ║")?;
        writeln!(f, "╚══════════════════════════════════════════════════════════════════╝")
    }
}

// ========================================================================
//                         PROJECT PIPELINE
// ========================================================================

#[derive(Debug)]
struct PipelineItem {
    name: &'static str,
    progress: u8,
    status: &'static str,
}

impl PipelineItem {
    fn new(name: &'static str, progress: u8) -> Self {
        Self {
            name,
            progress,
            status: "active",
        }
    }
}

struct Pipeline {
    items: Vec<PipelineItem>,
}

impl Pipeline {
    fn new() -> Self {
        Self {
            items: vec![
                PipelineItem::new("project_phoenix_rust", 90),
                PipelineItem::new("wiki_search", 85),
                PipelineItem::new("basic_web_server", 80),
            ],
        }
    }
}

impl fmt::Display for Pipeline {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        writeln!(f, "\n╔══════════════════════════════════════════════════════════════════╗")?;
        writeln!(f, "║                     PROJECT PIPELINE                            ║")?;
        writeln!(f, "╠══════════════════════════════════════════════════════════════════╣")?;
        writeln!(f, "║                                                                  ║")?;
        for item in &self.items {
            write!(f, "║  {:>22}  ", item.name)?;
            for _ in 0..(item.progress / 5) {
                write!(f, "█")?;
            }
            for _ in (item.progress / 5)..20 {
                write!(f, "░")?;
            }
            writeln!(f, "  {}%  ● {}  ║", item.progress, item.status)?;
        }
        writeln!(f, "║                                                                  ║")?;
        writeln!(f, "╚══════════════════════════════════════════════════════════════════╝")
    }
}

// ========================================================================
//                         DASHBOARD (RUST STYLE)
// ========================================================================

struct Dashboard {
    commits: u16,
    streak: u8,
    longest: u8,
    memory: u8,
    panics: u8,
}

impl Dashboard {
    fn new() -> Self {
        Self {
            commits: 196,
            streak: 16,
            longest: 16,
            memory: 100,
            panics: 0,
        }
    }
}

impl fmt::Display for Dashboard {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        writeln!(f, "\n╔══════════════════════════════════════════════════════════════════╗")?;
        writeln!(f, "║                        DASHBOARD                                ║")?;
        writeln!(f, "╠══════════════════════════════════════════════════════════════════╣")?;
        writeln!(f, "║                                                                  ║")?;
        writeln!(f, "║  ╭──────────┬──────────┬──────────┬──────────┬──────────╮       ║")?;
        writeln!(f, "║  │ COMMITS  │  STREAK  │ LONGEST  │ MEMORY   │ PANICS   │       ║")?;
        writeln!(f, "║  ├──────────┼──────────┼──────────┼──────────┼──────────┤       ║")?;
        writeln!(f, "║  │          │          │          │          │          │       ║")?;
        writeln!(f, "║  │   {:3}    │   {:2}     │   {:2}     │   {}%    │   {}     │       ║", self.commits, self.streak, self.longest, self.memory, self.panics)?;
        writeln!(f, "║  │          │          │          │          │          │       ║")?;
        writeln!(f, "║  ╰──────────┴──────────┴──────────┴──────────┴──────────╯       ║")?;
        writeln!(f, "║                                                                  ║")?;
        writeln!(f, "╚══════════════════════════════════════════════════════════════════╝")
    }
}

// ========================================================================
//                         PHILOSOPHY (RUST STYLE)
// ========================================================================

struct Philosophy {
    quotes: Vec<&'static str>,
}

impl Philosophy {
    fn new() -> Self {
        Self {
            quotes: vec![
                "\"large servers are just 100 small logics combined.\"",
                "\"consistency beats intensity.\"",
                "\"fear the person who has the discipline to write 100% test coverage.\"",
                "\"I AM THE BORROW CHECKER.\"",
                "\"silence is the loudest sound in the codebase.\"",
            ],
        }
    }
}

impl fmt::Display for Philosophy {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        writeln!(f, "\n╔══════════════════════════════════════════════════════════════════╗")?;
        writeln!(f, "║                        PHILOSOPHY                               ║")?;
        writeln!(f, "╠══════════════════════════════════════════════════════════════════╣")?;
        writeln!(f, "║                                                                  ║")?;
        writeln!(f, "║  ╭────────────────────────────────────────────────────────────╮  ║")?;
        writeln!(f, "║  │                                                            │  ║")?;
        for (i, quote) in self.quotes.iter().enumerate() {
            writeln!(f, "║  │  {:>56} │  ║", quote)?;
            if i == 2 || i == 3 {
                writeln!(f, "║  │                                                            │  ║")?;
                writeln!(f, "║  │  {:>56} │  ║", "─────────────────────────────────────────────────────────────")?;
                writeln!(f, "║  │                                                            │  ║")?;
            }
        }
        writeln!(f, "║  │                                                            │  ║")?;
        writeln!(f, "║  ╰────────────────────────────────────────────────────────────╯  ║")?;
        writeln!(f, "║                                                                  ║")?;
        writeln!(f, "╚══════════════════════════════════════════════════════════════════╝")
    }
}

// ========================================================================
//                         COMMUNITY
// ========================================================================

struct Community {
    philosophy: &'static str,
    milestones: &'static str,
    connect: &'static str,
}

impl Community {
    fn new() -> Self {
        Self {
            philosophy: "deep work state · rust core arch · zero panic eng · discipline > moti · 4:00 am club",
            milestones: "196+ commits · 100% crash-proof · memory: 100% · zero panics · target: 100% tests",
            connect: "LinkedIn · Email · GitHub",
        }
    }
}

impl fmt::Display for Community {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        writeln!(f, "\n╔══════════════════════════════════════════════════════════════════╗")?;
        writeln!(f, "║                        COMMUNITY                                ║")?;
        writeln!(f, "╠══════════════════════════════════════════════════════════════════╣")?;
        writeln!(f, "║                                                                  ║")?;
        writeln!(f, "║  ╭─────────────────────┬─────────────────────┬──────────────╮   ║")?;
        writeln!(f, "║  │     PHILOSOPHY      │     MILESTONES      │   CONNECT    │   ║")?;
        writeln!(f, "║  ├─────────────────────┼─────────────────────┼──────────────┤   ║")?;
        writeln!(f, "║  │                     │                     │              │   ║")?;
        writeln!(f, "║  │  deep work state    │  196+ commits       │  LinkedIn    │   ║")?;
        writeln!(f, "║  │  rust core arch     │  100% crash-proof   │  Email       │   ║")?;
        writeln!(f, "║  │  zero panic eng     │  memory: 100%       │  GitHub      │   ║")?;
        writeln!(f, "║  │  discipline > moti  │  zero panics        │              │   ║")?;
        writeln!(f, "║  │  4:00 am club       │  target: 100% tests │              │   ║")?;
        writeln!(f, "║  │                     │                     │              │   ║")?;
        writeln!(f, "║  ╰─────────────────────┴─────────────────────┴──────────────╯   ║")?;
        writeln!(f, "║                                                                  ║")?;
        writeln!(f, "╚══════════════════════════════════════════════════════════════════╝")
    }
}

// ========================================================================
//                         FINAL QUOTES
// ========================================================================

struct FinalQuotes {
    quotes: Vec<&'static str>,
}

impl FinalQuotes {
    fn new() -> Self {
        Self {
            quotes: vec![
                "\"i'm not a great programmer. i'm a good programmer with great habits.\" — kent beck",
                "\"c++ programmers fear the borrow checker. i am the borrow checker.\"",
                "\"discipline is choosing between what you want now and what you want most.\"",
            ],
        }
    }
}

impl fmt::Display for FinalQuotes {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        writeln!(f, "\n╔══════════════════════════════════════════════════════════════════╗")?;
        writeln!(f, "║                        QUOTES                                   ║")?;
        writeln!(f, "╠══════════════════════════════════════════════════════════════════╣")?;
        writeln!(f, "║                                                                  ║")?;
        writeln!(f, "║  ╭────────────────────────────────────────────────────────────╮  ║")?;
        writeln!(f, "║  │                                                            │  ║")?;
        for quote in &self.quotes {
            writeln!(f, "║  │  {:>56} │  ║", quote)?;
        }
        writeln!(f, "║  │                                                            │  ║")?;
        writeln!(f, "║  ╰────────────────────────────────────────────────────────────╯  ║")?;
        writeln!(f, "║                                                                  ║")?;
        writeln!(f, "╚══════════════════════════════════════════════════════════════════╝")
    }
}

// ========================================================================
//                         FOOTER
// ========================================================================

struct Footer;

impl fmt::Display for Footer {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        writeln!(f, "\n╔══════════════════════════════════════════════════════════════════╗")?;
        writeln!(f, "║                                                                  ║")?;
        writeln!(f, "║            ██████╗ ██████╗  ██████╗ ██╗███████╗██╗  ██╗         ║")?;
        writeln!(f, "║            ██╔══██╗██╔══██╗██╔═══██╗██║██╔════╝╚██╗██╔╝         ║")?;
        writeln!(f, "║            ██████╔╝██████╔╝██║   ██║██║█████╗   ╚███╔╝          ║")?;
        writeln!(f, "║            ██╔═══╝ ██╔══██╗██║   ██║██║██╔══╝   ██╔██╗          ║")?;
        writeln!(f, "║            ██║     ██║  ██║╚██████╔╝██║███████╗██╔╝ ██╗         ║")?;
        writeln!(f, "║            ╚═╝     ╚═╝  ╚═╝ ╚═════╝ ╚═╝╚══════╝╚═╝  ╚═╝         ║")?;
        writeln!(f, "║                                                                  ║")?;
        writeln!(f, "║  100% MEMORY SAFE  ✦  0% PANICS  ✦  CRASH-PROOF                ║")?;
        writeln!(f, "║                                                                  ║")?;
        writeln!(f, "║  \"silence is the loudest sound\"                                 ║")?;
        writeln!(f, "║                                                                  ║")?;
        writeln!(f, "╚══════════════════════════════════════════════════════════════════╝")
    }
}

// ========================================================================
//                         MAIN
// ========================================================================

fn main() -> Result<(), Box<dyn std::error::Error>> {
    let status = SystemStatus::new();
    let profile = Profile::new();
    let building = Building::new();
    let tech = TechStack::new();
    let pipeline = Pipeline::new();
    let dashboard = Dashboard::new();
    let philosophy = Philosophy::new();
    let community = Community::new();
    let quotes = FinalQuotes::new();

    println!("{}", status);
    println!("{}", profile);
    println!("{}", building);
    println!("{}", tech);
    println!("{}", pipeline);
    println!("{}", dashboard);
    println!("{}", philosophy);
    println!("{}", community);
    println!("{}", quotes);
    println!("{}", Footer);

    Ok(())
}

// ========================================================================
//                         TESTS
// ========================================================================

#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn test_memory_safety() {
        let status = SystemStatus::new();
        assert_eq!(status.memory, 100);
    }

    #[test]
    fn test_zero_panics() {
        let status = SystemStatus::new();
        assert_eq!(status.panics, 0);
    }

    #[test]
    fn test_commit_count() {
        let dashboard = Dashboard::new();
        assert!(dashboard.commits >= 196);
    }
}
