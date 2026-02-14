<!-- <!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <title>For You, Gulnaaz</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@400;700&family=Quicksand:wght@300;400;500;600&family=Great+Vibes&display=swap');

    * { margin: 0; padding: 0; box-sizing: border-box; }

    html {
      scroll-behavior: smooth;
      scroll-snap-type: y mandatory;
      overflow-x: hidden;
    }

    body {
      font-family: 'Quicksand', sans-serif;
      background: #1a0011;
      color: #fff;
      overflow-x: hidden;
    }

    /* ============ GLOBAL ANIMATIONS ============ */
    @keyframes heartBeat {
      0%, 100% { transform: scale(1); }
      15% { transform: scale(1.15); }
      30% { transform: scale(1); }
      45% { transform: scale(1.1); }
    }

    @keyframes softPulse {
      0%, 100% { opacity: 0.5; }
      50% { opacity: 1; }
    }

    @keyframes gradientShift {
      0%, 100% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
    }

    @keyframes floatUp {
      0% { transform: translateY(0) rotate(0deg) scale(1); opacity: 0; }
      10% { opacity: 0.7; }
      90% { opacity: 0.3; }
      100% { transform: translateY(-110vh) rotate(360deg) scale(0.5); opacity: 0; }
    }

    @keyframes sparkleAnim {
      0%, 100% { opacity: 0; transform: scale(0); }
      50% { opacity: 1; transform: scale(1); }
    }

    @keyframes slideUp {
      from { opacity: 0; transform: translateY(30px); }
      to { opacity: 1; transform: translateY(0); }
    }

    @keyframes fadeIn {
      to { opacity: 1; }
    }

    @keyframes spinBorder {
      to { transform: rotate(360deg); }
    }

    @keyframes typewriter {
      from { width: 0; }
      to { width: 100%; }
    }

    @keyframes blink {
      50% { border-color: transparent; }
    }

    @keyframes burstAnim {
      0% { opacity: 1; transform: translate(0,0) scale(1) rotate(0deg); }
      100% { opacity: 0; transform: translate(var(--tx), var(--ty)) scale(0) rotate(360deg); }
    }

    @keyframes confettiFall {
      0% { opacity: 1; transform: translateY(0) rotate(0deg); }
      100% { opacity: 0; transform: translateY(100vh) rotate(720deg); }
    }

    @keyframes orbFloat {
      0%, 100% { transform: translate(0, 0); }
      25% { transform: translate(30px, -30px); }
      50% { transform: translate(-20px, 20px); }
      75% { transform: translate(20px, 10px); }
    }

    @keyframes shineSlide {
      0% { transform: translateX(-100%); }
      100% { transform: translateX(100%); }
    }

    @keyframes ringPulse {
      0% { transform: translate(-50%, -50%) scale(0.8); opacity: 1; }
      100% { transform: translate(-50%, -50%) scale(2.2); opacity: 0; }
    }

    @keyframes cardShimmer {
      to { transform: rotate(360deg); }
    }

    @keyframes bounceIn {
      0% { transform: scale(0); opacity: 0; }
      50% { transform: scale(1.15); }
      70% { transform: scale(0.95); }
      100% { transform: scale(1); opacity: 1; }
    }

    @keyframes swing {
      0%, 100% { transform: rotate(-3deg); }
      50% { transform: rotate(3deg); }
    }

    @keyframes drawLine {
      to { stroke-dashoffset: 0; }
    }

    @keyframes countUp {
      from { content: "0"; }
    }

    @keyframes flipIn {
      0% { transform: perspective(400px) rotateY(90deg); opacity: 0; }
      100% { transform: perspective(400px) rotateY(0); opacity: 1; }
    }

    @keyframes glowPulse {
      0%, 100% { box-shadow: 0 0 20px rgba(255,107,157,0.3); }
      50% { box-shadow: 0 0 40px rgba(255,107,157,0.6), 0 0 60px rgba(232,67,147,0.3); }
    }

    /* ============ FLOATING ELEMENTS (global) ============ */
    .hearts-bg {
      position: fixed;
      inset: 0;
      pointer-events: none;
      z-index: 0;
      overflow: hidden;
    }

    .floating-heart {
      position: absolute;
      bottom: -60px;
      opacity: 0;
      animation: floatUp linear infinite;
      filter: blur(1px);
    }

    .sparkle {
      position: fixed;
      width: 4px; height: 4px;
      background: #fff;
      border-radius: 50%;
      pointer-events: none;
      z-index: 1;
      animation: sparkleAnim 2s ease-in-out infinite;
    }

    .glow-orb {
      position: fixed;
      border-radius: 50%;
      pointer-events: none;
      z-index: 0;
      filter: blur(60px);
      animation: orbFloat 8s ease-in-out infinite;
    }

    .burst-heart {
      position: fixed;
      font-size: 1.5rem;
      pointer-events: none;
      z-index: 999;
      animation: burstAnim 1.2s ease-out forwards;
    }

    .confetti {
      position: fixed;
      pointer-events: none;
      z-index: 998;
      animation: confettiFall linear forwards;
    }

    /* ============ SCROLL INDICATOR ============ */
    .scroll-indicator {
      position: fixed;
      bottom: 15px;
      left: 50%;
      transform: translateX(-50%);
      z-index: 90;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 5px;
      animation: softPulse 2s ease-in-out infinite;
      pointer-events: none;
      transition: opacity 0.3s ease;
    }

    .scroll-indicator span {
      font-family: 'Quicksand', sans-serif;
      font-size: 0.7rem;
      color: #ff8fbf;
      letter-spacing: 2px;
      text-transform: uppercase;
    }

    .scroll-arrow {
      width: 20px; height: 20px;
      border-right: 2px solid #ff8fbf;
      border-bottom: 2px solid #ff8fbf;
      transform: rotate(45deg);
      animation: bounceArrow 1.5s ease-in-out infinite;
    }

    @keyframes bounceArrow {
      0%, 100% { transform: rotate(45deg) translateY(0); }
      50% { transform: rotate(45deg) translateY(5px); }
    }

    /* ============ SECTION BASE ============ */
    .section {
      min-height: 100dvh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 30px 20px;
      position: relative;
      scroll-snap-align: start;
      overflow: hidden;
    }

    /* ============ SECTION 1: ENVELOPE INTRO ============ */
    .envelope-screen {
      position: fixed;
      inset: 0;
      z-index: 100;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      background: linear-gradient(135deg, #1a0011, #2d0a1e, #1a0011);
      transition: opacity 0.8s ease, visibility 0.8s ease;
    }

    .envelope-screen.hide {
      opacity: 0;
      visibility: hidden;
      pointer-events: none;
    }

    .envelope-for-text {
      font-family: 'Great Vibes', cursive;
      font-size: 1.6rem;
      color: #ffb6d3;
      margin-bottom: 20px;
      opacity: 0;
      animation: slideUp 1s ease forwards 0.5s;
    }

    .envelope-container {
      position: relative;
      width: 220px;
      height: 160px;
      cursor: pointer;
      animation: envelopeBounce 2s ease-in-out infinite;
    }

    @keyframes envelopeBounce {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-10px); }
    }

    .envelope-body {
      width: 100%; height: 100%;
      background: linear-gradient(145deg, #ff6b9d, #e84393);
      border-radius: 10px;
      position: relative;
      box-shadow: 0 10px 40px rgba(232,67,147,0.4);
    }

    .envelope-flap {
      position: absolute; top: 0; left: 0;
      width: 100%; height: 50%;
      background: linear-gradient(145deg, #ff85ad, #e84393);
      clip-path: polygon(0 0, 50% 100%, 100% 0);
      transform-origin: top center;
      transition: transform 0.6s ease;
      z-index: 2;
    }

    .envelope-container.opened .envelope-flap { transform: rotateX(180deg); }

    .envelope-heart-icon {
      position: absolute; top: 50%; left: 50%;
      transform: translate(-50%, -50%);
      font-size: 3rem; z-index: 1;
      animation: heartBeat 1.2s ease-in-out infinite;
    }

    .envelope-letter {
      position: absolute; bottom: 10px; left: 50%;
      transform: translateX(-50%);
      width: 80%; height: 40px;
      background: #fff; border-radius: 4px;
      transition: transform 0.6s ease 0.3s, height 0.4s ease 0.3s;
      z-index: 3;
    }

    .envelope-container.opened .envelope-letter {
      transform: translateX(-50%) translateY(-120px);
      height: 80px;
    }

    .letter-text {
      color: #e84393;
      font-family: 'Dancing Script', cursive;
      font-size: 0.85rem;
      text-align: center;
      padding: 10px;
      opacity: 0;
      transition: opacity 0.4s ease 0.8s;
    }

    .envelope-container.opened .letter-text { opacity: 1; }

    .envelope-tap-text {
      font-family: 'Dancing Script', cursive;
      font-size: 1.2rem;
      color: #ff8fbf;
      margin-top: 30px;
      animation: softPulse 2s ease-in-out infinite;
    }

    /* ============ SECTION 2: MAIN VALENTINE ============ */
    .s-valentine {
      background: linear-gradient(135deg, #1a0011, #2d0a1e, #1a0011);
    }

    .names-together {
      font-family: 'Great Vibes', cursive;
      font-size: clamp(1.4rem, 5vw, 2rem);
      color: #ffb6d3;
      margin-bottom: 10px;
      opacity: 0;
      animation: slideUp 1s ease forwards 0.3s;
    }

    .names-together .amp {
      color: #ff6b9d;
      font-size: 1.4em;
      margin: 0 5px;
      display: inline-block;
      animation: heartBeat 1.2s ease-in-out infinite;
    }

    .photo-frame {
      width: 110px; height: 110px;
      border-radius: 50%;
      border: 3px solid rgba(255,107,157,0.5);
      padding: 4px;
      margin: 0 auto 12px;
      opacity: 0;
      animation: bounceIn 0.8s ease forwards 0.5s;
      position: relative;
      display: flex;
      align-items: center;
      justify-content: center;
      background: rgba(255,107,157,0.1);
      cursor: pointer;
    }

    .photo-frame::after {
      content: '';
      position: absolute; inset: -3px;
      border-radius: 50%;
      border: 2px solid transparent;
      border-top-color: #ff6b9d;
      animation: spinBorder 3s linear infinite;
    }

    .couple-emoji { font-size: 2.8rem; }

    .big-heart-container {
      position: relative;
      margin-bottom: 12px;
    }

    .big-heart {
      font-size: 4rem;
      display: inline-block;
      animation: heartBeat 1.2s ease-in-out infinite;
      filter: drop-shadow(0 0 20px rgba(255,107,157,0.6));
      cursor: pointer;
    }

    .heart-ring {
      position: absolute; top: 50%; left: 50%;
      transform: translate(-50%, -50%);
      width: 100px; height: 100px;
      border: 2px solid rgba(255,107,157,0.4);
      border-radius: 50%;
      animation: ringPulse 2s ease-out infinite;
    }

    .heart-ring:nth-child(2) { animation-delay: 0.5s; }
    .heart-ring:nth-child(3) { animation-delay: 1s; }

    .title {
      font-family: 'Dancing Script', cursive;
      font-size: clamp(2rem, 8vw, 3.2rem);
      font-weight: 700;
      background: linear-gradient(135deg, #ff6b9d, #ff8fbf, #ffb6d3, #ff6b9d);
      background-size: 300% 300%;
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      animation: gradientShift 4s ease infinite;
      margin-bottom: 5px;
      line-height: 1.3;
    }

    .subtitle {
      font-family: 'Great Vibes', cursive;
      font-size: clamp(1.1rem, 4.5vw, 1.6rem);
      color: #ff8fbf;
      margin-bottom: 15px;
      opacity: 0;
      animation: slideUp 1s ease forwards 1s;
    }

    .message-card {
      background: rgba(255,255,255,0.06);
      backdrop-filter: blur(15px);
      -webkit-backdrop-filter: blur(15px);
      border: 1px solid rgba(255,107,157,0.2);
      border-radius: 20px;
      padding: 20px 18px;
      max-width: 340px;
      width: 90%;
      margin: 0 auto 15px;
      opacity: 0;
      animation: slideUp 1s ease forwards 1.3s;
      position: relative;
      overflow: hidden;
    }

    .message-card::before {
      content: '';
      position: absolute; top: -50%; left: -50%;
      width: 200%; height: 200%;
      background: conic-gradient(from 0deg, transparent, rgba(255,107,157,0.1), transparent, rgba(255,143,191,0.1), transparent);
      animation: cardShimmer 6s linear infinite;
    }

    .message-text {
      position: relative; z-index: 1;
      font-size: clamp(0.85rem, 3.5vw, 1rem);
      line-height: 1.8;
      color: #ffd6e7;
      font-weight: 300;
    }

    .message-text .highlight {
      color: #ff6b9d;
      font-weight: 600;
      font-family: 'Dancing Script', cursive;
      font-size: 1.2em;
    }

    /* ============ SECTION 3: REASONS I LOVE YOU ============ */
    .s-reasons {
      background: linear-gradient(180deg, #1a0011, #220a18, #1a0011);
    }

    .section-heading {
      font-family: 'Dancing Script', cursive;
      font-size: clamp(1.5rem, 6vw, 2.2rem);
      background: linear-gradient(135deg, #ff6b9d, #ffb6d3);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      margin-bottom: 20px;
      text-align: center;
    }

    .reasons-container {
      display: flex;
      flex-direction: column;
      gap: 12px;
      max-width: 340px;
      width: 90%;
    }

    .reason-card {
      background: rgba(255,255,255,0.05);
      border: 1px solid rgba(255,107,157,0.15);
      border-radius: 16px;
      padding: 14px 16px;
      display: flex;
      align-items: center;
      gap: 12px;
      cursor: pointer;
      transition: all 0.3s ease;
      opacity: 0;
      transform: translateX(-30px);
      position: relative;
      overflow: hidden;
    }

    .reason-card.visible {
      opacity: 1;
      transform: translateX(0);
    }

    .reason-card:active {
      transform: scale(0.97);
      background: rgba(255,107,157,0.15);
    }

    .reason-card.tapped {
      background: rgba(255,107,157,0.12);
      border-color: rgba(255,107,157,0.4);
    }

    .reason-card.tapped::after {
      content: '';
      position: absolute; inset: 0;
      background: linear-gradient(90deg, transparent, rgba(255,107,157,0.1), transparent);
      animation: shineSlide 1.5s ease;
    }

    .reason-num {
      width: 32px; height: 32px;
      background: linear-gradient(135deg, #ff6b9d, #e84393);
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 0.8rem;
      font-weight: 600;
      flex-shrink: 0;
    }

    .reason-text {
      font-size: 0.9rem;
      color: #ffd6e7;
      line-height: 1.4;
    }

    .reason-emoji {
      font-size: 1.3rem;
      margin-left: auto;
      flex-shrink: 0;
      transition: transform 0.3s ease;
    }

    .reason-card.tapped .reason-emoji {
      animation: bounceIn 0.5s ease;
    }

    /* ============ SECTION 4: LOVE CALCULATOR ============ */
    .s-calculator {
      background: linear-gradient(180deg, #1a0011, #250d1c, #1a0011);
    }

    .calc-card {
      background: rgba(255,255,255,0.05);
      backdrop-filter: blur(15px);
      -webkit-backdrop-filter: blur(15px);
      border: 1px solid rgba(255,107,157,0.2);
      border-radius: 24px;
      padding: 25px 20px;
      max-width: 340px;
      width: 90%;
      text-align: center;
    }

    .calc-names {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      margin-bottom: 20px;
    }

    .calc-name {
      font-family: 'Great Vibes', cursive;
      font-size: 1.4rem;
      color: #ffb6d3;
      padding: 6px 16px;
      border: 1px solid rgba(255,107,157,0.3);
      border-radius: 20px;
      background: rgba(255,107,157,0.08);
    }

    .calc-heart {
      font-size: 1.5rem;
      animation: heartBeat 1.2s ease-in-out infinite;
    }

    .calc-btn {
      background: linear-gradient(135deg, #ff6b9d, #e84393);
      border: none;
      padding: 12px 30px;
      border-radius: 50px;
      color: white;
      font-family: 'Dancing Script', cursive;
      font-size: 1.1rem;
      cursor: pointer;
      box-shadow: 0 5px 25px rgba(232,67,147,0.4);
      transition: transform 0.3s ease;
      margin-bottom: 20px;
      animation: glowPulse 2s ease-in-out infinite;
    }

    .calc-btn:active { transform: scale(0.95); }

    .calc-result {
      display: none;
      flex-direction: column;
      align-items: center;
      gap: 10px;
    }

    .calc-result.show { display: flex; }

    .calc-percentage {
      font-family: 'Dancing Script', cursive;
      font-size: 3rem;
      color: #ff6b9d;
      font-weight: 700;
    }

    .calc-bar-track {
      width: 100%;
      height: 16px;
      background: rgba(255,255,255,0.1);
      border-radius: 10px;
      overflow: hidden;
    }

    .calc-bar-fill {
      height: 100%;
      width: 0%;
      background: linear-gradient(90deg, #ff6b9d, #e84393, #ff6b9d);
      background-size: 200% 100%;
      border-radius: 10px;
      transition: width 2s ease;
      position: relative;
    }

    .calc-bar-fill::after {
      content: '';
      position: absolute; inset: 0;
      background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
      animation: shineSlide 2s ease-in-out infinite;
    }

    .calc-msg {
      font-family: 'Dancing Script', cursive;
      font-size: 1.1rem;
      color: #ffb6d3;
      opacity: 0;
      transition: opacity 0.5s ease;
    }

    .calc-msg.show { opacity: 1; }

    /* ============ SECTION 5: PROMISE CARDS (swipeable) ============ */
    .s-promises {
      background: linear-gradient(180deg, #1a0011, #1f0815, #1a0011);
    }

    .promise-carousel {
      position: relative;
      width: 90%;
      max-width: 320px;
      height: 200px;
      perspective: 800px;
    }

    .promise-card {
      position: absolute;
      inset: 0;
      background: rgba(255,255,255,0.06);
      backdrop-filter: blur(15px);
      -webkit-backdrop-filter: blur(15px);
      border: 1px solid rgba(255,107,157,0.2);
      border-radius: 20px;
      padding: 25px 20px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      text-align: center;
      transition: all 0.5s ease;
      cursor: pointer;
      opacity: 0;
      transform: scale(0.85) translateX(50px);
    }

    .promise-card.active {
      opacity: 1;
      transform: scale(1) translateX(0);
      z-index: 2;
    }

    .promise-card.prev {
      opacity: 0.3;
      transform: scale(0.85) translateX(-50px);
      z-index: 1;
    }

    .promise-card.next {
      opacity: 0.3;
      transform: scale(0.85) translateX(50px);
      z-index: 1;
    }

    .promise-emoji {
      font-size: 2.5rem;
      margin-bottom: 12px;
    }

    .promise-text {
      font-family: 'Dancing Script', cursive;
      font-size: 1.15rem;
      color: #ffd6e7;
      line-height: 1.5;
    }

    .promise-dots {
      display: flex;
      gap: 8px;
      margin-top: 20px;
    }

    .promise-dot {
      width: 8px; height: 8px;
      border-radius: 50%;
      background: rgba(255,107,157,0.3);
      transition: all 0.3s ease;
      cursor: pointer;
    }

    .promise-dot.active {
      background: #ff6b9d;
      transform: scale(1.3);
    }

    .promise-nav-hint {
      font-size: 0.75rem;
      color: #ff8fbf;
      margin-top: 10px;
      animation: softPulse 2s ease-in-out infinite;
    }

    /* ============ SECTION 6: SCRATCH CARD ============ */
    .s-scratch {
      background: linear-gradient(180deg, #1a0011, #2a0d1e, #1a0011);
    }

    .scratch-container {
      position: relative;
      width: 280px;
      height: 180px;
      border-radius: 20px;
      overflow: hidden;
      cursor: pointer;
      box-shadow: 0 10px 40px rgba(232,67,147,0.3);
    }

    .scratch-reveal {
      position: absolute; inset: 0;
      background: linear-gradient(135deg, #ff6b9d, #e84393);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      z-index: 0;
    }

    .scratch-reveal-emoji {
      font-size: 3rem;
      margin-bottom: 8px;
    }

    .scratch-reveal-text {
      font-family: 'Dancing Script', cursive;
      font-size: 1.3rem;
      color: #fff;
      text-align: center;
      padding: 0 15px;
    }

    .scratch-canvas {
      position: absolute; inset: 0;
      z-index: 1;
      border-radius: 20px;
    }

    .scratch-hint {
      font-size: 0.8rem;
      color: #ff8fbf;
      margin-top: 15px;
      animation: softPulse 2s ease-in-out infinite;
    }

    /* ============ SECTION 7: TIMELINE ============ */
    .s-timeline {
      background: linear-gradient(180deg, #1a0011, #200e18, #1a0011);
      padding: 40px 20px;
    }

    .timeline {
      position: relative;
      max-width: 320px;
      width: 90%;
    }

    .timeline::before {
      content: '';
      position: absolute;
      left: 15px;
      top: 0; bottom: 0;
      width: 2px;
      background: linear-gradient(180deg, #ff6b9d, #e84393, #ff6b9d);
    }

    .timeline-item {
      position: relative;
      padding-left: 45px;
      margin-bottom: 25px;
      opacity: 0;
      transform: translateX(-20px);
      transition: all 0.5s ease;
    }

    .timeline-item.visible {
      opacity: 1;
      transform: translateX(0);
    }

    .timeline-dot {
      position: absolute;
      left: 8px;
      top: 5px;
      width: 16px; height: 16px;
      background: #ff6b9d;
      border-radius: 50%;
      border: 3px solid #1a0011;
      z-index: 1;
    }

    .timeline-item.visible .timeline-dot {
      animation: glowPulse 2s ease-in-out infinite;
    }

    .timeline-label {
      font-family: 'Dancing Script', cursive;
      font-size: 0.85rem;
      color: #ff8fbf;
      margin-bottom: 4px;
    }

    .timeline-content {
      font-size: 0.9rem;
      color: #ffd6e7;
      line-height: 1.5;
    }

    .timeline-emoji {
      font-size: 1.2rem;
      margin-left: 5px;
    }

    /* ============ SECTION 8: FINAL - LOVE METER + ACTIONS ============ */
    .s-final {
      background: linear-gradient(180deg, #1a0011, #2d0a1e, #1a0011);
    }

    .final-heart {
      font-size: 5rem;
      animation: heartBeat 1.2s ease-in-out infinite;
      filter: drop-shadow(0 0 30px rgba(255,107,157,0.6));
      margin-bottom: 15px;
      cursor: pointer;
    }

    .final-title {
      font-family: 'Great Vibes', cursive;
      font-size: clamp(1.5rem, 6vw, 2.2rem);
      color: #ffb6d3;
      margin-bottom: 5px;
    }

    .final-subtitle {
      font-family: 'Dancing Script', cursive;
      font-size: 1rem;
      color: #ff8fbf;
      margin-bottom: 20px;
    }

    .love-meter {
      max-width: 280px;
      width: 85%;
      margin-bottom: 20px;
    }

    .love-meter-label {
      font-family: 'Dancing Script', cursive;
      font-size: 1rem;
      color: #ff8fbf;
      margin-bottom: 6px;
    }

    .meter-track {
      width: 100%;
      height: 14px;
      background: rgba(255,255,255,0.1);
      border-radius: 10px;
      overflow: hidden;
    }

    .meter-fill {
      height: 100%; width: 0%;
      background: linear-gradient(90deg, #ff6b9d, #e84393, #ff6b9d);
      background-size: 200% 100%;
      border-radius: 10px;
      transition: width 2s ease;
      position: relative;
    }

    .meter-fill::after {
      content: '';
      position: absolute; inset: 0;
      background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
      animation: shineSlide 2s ease-in-out infinite;
    }

    .meter-value {
      font-family: 'Dancing Script', cursive;
      font-size: 0.9rem;
      color: #ffb6d3;
      margin-top: 5px;
      text-align: right;
    }

    .action-buttons {
      display: flex;
      gap: 12px;
      flex-wrap: wrap;
      justify-content: center;
    }

    .action-btn {
      background: linear-gradient(135deg, #ff6b9d, #e84393);
      border: none;
      padding: 12px 22px;
      border-radius: 50px;
      color: white;
      font-family: 'Dancing Script', cursive;
      font-size: 1rem;
      cursor: pointer;
      box-shadow: 0 5px 20px rgba(232,67,147,0.3);
      transition: transform 0.3s ease;
    }

    .action-btn:active { transform: scale(0.93); }

    .action-btn.outline {
      background: transparent;
      border: 2px solid #ff6b9d;
    }

    /* ============ POPUP / MODAL ============ */
    .modal-overlay {
      position: fixed; inset: 0;
      background: rgba(0,0,0,0.7);
      backdrop-filter: blur(8px);
      -webkit-backdrop-filter: blur(8px);
      z-index: 200;
      display: none;
      align-items: center;
      justify-content: center;
      padding: 20px;
    }

    .modal-overlay.show {
      display: flex;
    }

    .modal-card {
      background: linear-gradient(135deg, #2d0a1e, #1a0011);
      border: 1px solid rgba(255,107,157,0.3);
      border-radius: 24px;
      padding: 30px 24px;
      max-width: 320px;
      width: 100%;
      text-align: center;
      animation: bounceIn 0.5s ease;
    }

    .modal-emoji {
      font-size: 3.5rem;
      margin-bottom: 12px;
    }

    .modal-title {
      font-family: 'Dancing Script', cursive;
      font-size: 1.4rem;
      color: #ff6b9d;
      margin-bottom: 10px;
    }

    .modal-text {
      font-size: 0.9rem;
      color: #ffd6e7;
      line-height: 1.6;
      margin-bottom: 18px;
    }

    .modal-close {
      background: linear-gradient(135deg, #ff6b9d, #e84393);
      border: none;
      padding: 10px 28px;
      border-radius: 50px;
      color: white;
      font-family: 'Dancing Script', cursive;
      font-size: 1rem;
      cursor: pointer;
    }

    /* ============ WISH JAR ============ */
    .s-wishjar {
      background: linear-gradient(180deg, #1a0011, #1e0b16, #1a0011);
    }

    .jar-container {
      position: relative;
      width: 180px;
      height: 220px;
      margin-bottom: 15px;
    }

    .jar-body {
      position: absolute;
      bottom: 0;
      left: 15px;
      right: 15px;
      height: 180px;
      background: rgba(255,255,255,0.06);
      border: 2px solid rgba(255,182,211,0.25);
      border-radius: 0 0 25px 25px;
      overflow: hidden;
    }

    .jar-lid {
      position: absolute;
      top: 25px;
      left: 5px;
      right: 5px;
      height: 20px;
      background: linear-gradient(135deg, #ff6b9d, #e84393);
      border-radius: 6px;
      box-shadow: 0 4px 15px rgba(232,67,147,0.3);
    }

    .jar-label {
      position: absolute;
      top: 0;
      left: 50%;
      transform: translateX(-50%);
      font-size: 1.5rem;
    }

    .jar-note {
      position: absolute;
      font-size: 1.2rem;
      animation: jarFloat 3s ease-in-out infinite;
      cursor: pointer;
      transition: transform 0.2s ease;
      z-index: 2;
    }

    .jar-note:active { transform: scale(1.3); }

    @keyframes jarFloat {
      0%, 100% { transform: translateY(0) rotate(-5deg); }
      50% { transform: translateY(-8px) rotate(5deg); }
    }

    .jar-tap-hint {
      font-size: 0.75rem;
      color: #ff8fbf;
      animation: softPulse 2s ease-in-out infinite;
    }

    /* ============ HUG COUNTER ============ */
    .hug-counter {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 5px;
      margin-top: 15px;
    }

    .hug-count-display {
      font-family: 'Dancing Script', cursive;
      font-size: 2rem;
      color: #ff6b9d;
    }

    .hug-label {
      font-size: 0.8rem;
      color: #ffb6d3;
    }

    /* ============ SMALL SCREEN ADJUSTMENTS ============ */
    @media (max-height: 700px) {
      .section { padding: 20px 15px; }
      .big-heart { font-size: 3rem; }
      .heart-ring { width: 80px; height: 80px; }
      .photo-frame { width: 85px; height: 85px; }
      .couple-emoji { font-size: 2.2rem; }
      .message-card { padding: 15px 14px; }
      .reason-card { padding: 10px 12px; }
      .promise-carousel { height: 170px; }
      .scratch-container { width: 250px; height: 160px; }
      .final-heart { font-size: 3.5rem; }
      .jar-container { width: 150px; height: 190px; }
    }

    @media (max-height: 600px) {
      .photo-frame { width: 65px; height: 65px; margin-bottom: 6px; }
      .couple-emoji { font-size: 1.6rem; }
      .big-heart { font-size: 2.5rem; }
      .big-heart-container { margin-bottom: 6px; }
      .message-card { margin-bottom: 10px; padding: 12px; }
      .promise-carousel { height: 150px; }
      .scratch-container { width: 220px; height: 140px; }
    }
  </style>
</head>
<body>

  <!-- ========== ENVELOPE INTRO ========== -->
  <div class="envelope-screen" id="envelopeScreen">
    <div class="envelope-for-text">For you, Gulnaaz...</div>
    <div class="envelope-container" id="envelope" onclick="openEnvelope()">
      <div class="envelope-flap"></div>
      <div class="envelope-body">
        <div class="envelope-heart-icon">💌</div>
      </div>
      <div class="envelope-letter">
        <div class="letter-text">A letter from Alam, just for you...</div>
      </div>
    </div>
    <div class="envelope-tap-text">Tap to open</div>
  </div>

  <!-- ========== GLOBAL BG ========== -->
  <div class="hearts-bg" id="heartsBg"></div>
  <div class="glow-orb" style="width:200px;height:200px;background:rgba(232,67,147,0.12);top:10%;left:-50px;"></div>
  <div class="glow-orb" style="width:150px;height:150px;background:rgba(255,107,157,0.08);bottom:15%;right:-30px;animation-delay:3s;"></div>

  <!-- ========== SCROLL INDICATOR ========== -->
  <div class="scroll-indicator" id="scrollIndicator" style="display:none;">
    <span>Scroll</span>
    <div class="scroll-arrow"></div>
  </div>

  <!-- ========== SECTION 1: VALENTINE MAIN ========== -->
  <div class="section s-valentine" id="sValentine">
    <div class="names-together">Alam <span class="amp">&</span> Gulnaaz</div>
    <div class="photo-frame" onclick="tapPhotoFrame(event)">
      <span class="couple-emoji">💑</span>
    </div>
    <div class="big-heart-container">
      <div class="heart-ring"></div>
      <div class="heart-ring"></div>
      <div class="heart-ring"></div>
      <div class="big-heart" onclick="tapHeart(event)">❤️</div>
    </div>
    <h1 class="title">Happy Valentine's Day</h1>
    <p class="subtitle">To my beautiful Gulnaaz</p>
    <div class="message-card">
      <p class="message-text">
        Every moment with you is a <span class="highlight">beautiful dream</span> I never want to wake up from.
        You make my world brighter, my heart fuller, and my life so much more
        <span class="highlight">meaningful</span>. I love you endlessly, Gulnaaz. 💕
      </p>
    </div>
  </div>

  <!-- ========== SECTION 2: REASONS I LOVE YOU ========== -->
  <div class="section s-reasons" id="sReasons">
    <div class="section-heading">Reasons I Love You</div>
    <div class="reasons-container" id="reasonsList">
      <div class="reason-card" onclick="tapReason(this, event)">
        <div class="reason-num">1</div>
        <div class="reason-text">Your smile lights up my darkest days</div>
        <div class="reason-emoji">😊</div>
      </div>
      <div class="reason-card" onclick="tapReason(this, event)">
        <div class="reason-num">2</div>
        <div class="reason-text">You believe in me when no one else does</div>
        <div class="reason-emoji">💪</div>
      </div>
      <div class="reason-card" onclick="tapReason(this, event)">
        <div class="reason-num">3</div>
        <div class="reason-text">Your laugh is my favorite sound</div>
        <div class="reason-emoji">🥰</div>
      </div>
      <div class="reason-card" onclick="tapReason(this, event)">
        <div class="reason-num">4</div>
        <div class="reason-text">You make even boring moments magical</div>
        <div class="reason-emoji">✨</div>
      </div>
      <div class="reason-card" onclick="tapReason(this, event)">
        <div class="reason-num">5</div>
        <div class="reason-text">You're my best friend and my whole world</div>
        <div class="reason-emoji">🌍</div>
      </div>
    </div>
  </div>

  <!-- ========== SECTION 3: LOVE CALCULATOR ========== -->
  <div class="section s-calculator" id="sCalculator">
    <div class="section-heading">Love Calculator</div>
    <div class="calc-card">
      <div class="calc-names">
        <div class="calc-name">Alam</div>
        <div class="calc-heart">💕</div>
        <div class="calc-name">Gulnaaz</div>
      </div>
      <button class="calc-btn" id="calcBtn" onclick="calculateLove()">Calculate Our Love</button>
      <div class="calc-result" id="calcResult">
        <div class="calc-percentage" id="calcPercent">0%</div>
        <div class="calc-bar-track">
          <div class="calc-bar-fill" id="calcBar"></div>
        </div>
        <div class="calc-msg" id="calcMsg">Made for each other, forever!</div>
      </div>
    </div>
  </div>

  <!-- ========== SECTION 4: PROMISES CAROUSEL ========== -->
  <div class="section s-promises" id="sPromises">
    <div class="section-heading">My Promises To You</div>
    <div class="promise-carousel" id="promiseCarousel">
      <div class="promise-card" data-idx="0">
        <div class="promise-emoji">🌹</div>
        <div class="promise-text">I promise to always make you feel loved, even on your worst days.</div>
      </div>
      <div class="promise-card" data-idx="1">
        <div class="promise-emoji">🤗</div>
        <div class="promise-text">I promise to hold you close and never let you feel alone.</div>
      </div>
      <div class="promise-card" data-idx="2">
        <div class="promise-emoji">🌙</div>
        <div class="promise-text">I promise to be your peace in every storm and your warmth on cold nights.</div>
      </div>
      <div class="promise-card" data-idx="3">
        <div class="promise-emoji">💎</div>
        <div class="promise-text">I promise to cherish you today, tomorrow, and every day after.</div>
      </div>
      <div class="promise-card" data-idx="4">
        <div class="promise-emoji">🔐</div>
        <div class="promise-text">I promise that my heart belongs only to you, Gulnaaz. Always.</div>
      </div>
    </div>
    <div class="promise-dots" id="promiseDots"></div>
    <div class="promise-nav-hint">Tap to see next promise</div>
  </div>

  <!-- ========== SECTION 5: WISH JAR ========== -->
  <div class="section s-wishjar" id="sWishJar">
    <div class="section-heading">Our Wish Jar</div>
    <div class="jar-container" id="jarContainer">
      <div class="jar-label">🏺</div>
      <div class="jar-lid"></div>
      <div class="jar-body" id="jarBody"></div>
    </div>
    <div class="jar-tap-hint">Tap the notes inside the jar!</div>
  </div>

  <!-- ========== SECTION 6: SCRATCH CARD ========== -->
  <div class="section s-scratch" id="sScratch">
    <div class="section-heading">A Secret For You</div>
    <div class="scratch-container" id="scratchContainer">
      <div class="scratch-reveal">
        <div class="scratch-reveal-emoji">👑</div>
        <div class="scratch-reveal-text">You are the queen of my heart, Gulnaaz. I'm so lucky you're mine!</div>
      </div>
      <canvas class="scratch-canvas" id="scratchCanvas"></canvas>
    </div>
    <div class="scratch-hint">Scratch to reveal the secret!</div>
  </div>

  <!-- ========== SECTION 7: TIMELINE ========== -->
  <div class="section s-timeline" id="sTimeline">
    <div class="section-heading">Our Love Story</div>
    <div class="timeline" id="timeline">
      <div class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="timeline-label">The Beginning</div>
        <div class="timeline-content">The day I first saw you, my world changed forever <span class="timeline-emoji">💫</span></div>
      </div>
      <div class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="timeline-label">First Butterflies</div>
        <div class="timeline-content">Every conversation made me fall for you a little more <span class="timeline-emoji">🦋</span></div>
      </div>
      <div class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="timeline-label">Falling In Love</div>
        <div class="timeline-content">I realized you weren't just special — you were everything <span class="timeline-emoji">💖</span></div>
      </div>
      <div class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="timeline-label">Today & Forever</div>
        <div class="timeline-content">I love you more than yesterday, less than tomorrow <span class="timeline-emoji">♾️</span></div>
      </div>
    </div>
  </div>

  <!-- ========== SECTION 8: FINAL ========== -->
  <div class="section s-final" id="sFinal">
    <div class="final-heart" onclick="tapFinalHeart(event)">💝</div>
    <div class="final-title">Forever Yours, Gulnaaz</div>
    <div class="final-subtitle">— With all my love, Alam</div>
    <div class="love-meter" id="loveMeter">
      <div class="love-meter-label">Alam's Love For Gulnaaz</div>
      <div class="meter-track">
        <div class="meter-fill" id="meterFill"></div>
      </div>
      <div class="meter-value">Infinity & Beyond 💗</div>
    </div>
    <div class="action-buttons">
      <button class="action-btn" onclick="sendKiss(event)">Send a Kiss 💋</button>
      <button class="action-btn outline" onclick="sendHug(event)">Send a Hug 🤗</button>
    </div>
    <div class="hug-counter" id="hugCounter" style="display:none;">
      <div class="hug-count-display" id="hugCountDisplay">0</div>
      <div class="hug-label">virtual hugs sent!</div>
    </div>
  </div>

  <!-- ========== MODALS ========== -->
  <div class="modal-overlay" id="modalOverlay" onclick="closeModal(event)">
    <div class="modal-card" onclick="event.stopPropagation()">
      <div class="modal-emoji" id="modalEmoji">💕</div>
      <div class="modal-title" id="modalTitle">Title</div>
      <div class="modal-text" id="modalText">Text</div>
      <button class="modal-close" onclick="closeModal()">Close</button>
    </div>
  </div>

  <script>
    // ============ ENVELOPE ============
    let envelopeOpened = false;

    function openEnvelope() {
      if (envelopeOpened) return;
      envelopeOpened = true;
      document.getElementById('envelope').classList.add('opened');
      const rect = document.getElementById('envelope').getBoundingClientRect();
      for (let i = 0; i < 15; i++) createBurstHeart(rect.left + rect.width/2, rect.top + rect.height/2);
      setTimeout(() => {
        document.getElementById('envelopeScreen').classList.add('hide');
        document.getElementById('scrollIndicator').style.display = 'flex';
        startBackgroundHearts();
        startSparkles();
        observeSections();
        initScratchCard();
        initWishJar();
        initPromises();
      }, 1500);
    }

    // ============ BACKGROUND HEARTS ============
    function startBackgroundHearts() {
      const container = document.getElementById('heartsBg');
      const hearts = ['💕','💖','💗','💓','💘','💝','🩷','♥️'];
      function spawn() {
        const h = document.createElement('div');
        h.classList.add('floating-heart');
        h.textContent = hearts[Math.floor(Math.random()*hearts.length)];
        h.style.left = Math.random()*100+'%';
        h.style.fontSize = (Math.random()*18+12)+'px';
        h.style.animationDuration = (Math.random()*6+6)+'s';
        container.appendChild(h);
        setTimeout(() => h.remove(), 12000);
      }
      for(let i=0;i<6;i++) setTimeout(spawn, i*400);
      setInterval(spawn, 1500);
    }

    // ============ SPARKLES ============
    function startSparkles() {
      function spawn() {
        const s = document.createElement('div');
        s.classList.add('sparkle');
        s.style.left = Math.random()*100+'vw';
        s.style.top = Math.random()*100+'vh';
        s.style.animationDuration = (Math.random()*2+1)+'s';
        s.style.width = s.style.height = (Math.random()*4+2)+'px';
        document.body.appendChild(s);
        setTimeout(() => s.remove(), 3000);
      }
      for(let i=0;i<10;i++) setTimeout(spawn, i*200);
      setInterval(spawn, 500);
    }

    // ============ BURST HEARTS ============
    function createBurstHeart(x, y) {
      const el = document.createElement('div');
      el.classList.add('burst-heart');
      el.textContent = ['❤️','💕','💖','💗','💋','🩷','✨'][Math.floor(Math.random()*7)];
      el.style.left = x+'px'; el.style.top = y+'px';
      const a = Math.random()*Math.PI*2, d = Math.random()*120+60;
      el.style.setProperty('--tx', Math.cos(a)*d+'px');
      el.style.setProperty('--ty', Math.sin(a)*d+'px');
      document.body.appendChild(el);
      setTimeout(() => el.remove(), 1200);
    }

    // ============ CONFETTI ============
    function createConfetti() {
      const c = document.createElement('div');
      c.classList.add('confetti');
      c.style.background = ['#ff6b9d','#e84393','#ff8fbf','#ffb6d3','#fff','#ffd6e7'][Math.floor(Math.random()*6)];
      c.style.left = Math.random()*100+'vw';
      c.style.top = '-10px';
      c.style.width = (Math.random()*8+4)+'px';
      c.style.height = (Math.random()*8+4)+'px';
      c.style.borderRadius = Math.random()>0.5?'50%':'2px';
      c.style.animationDuration = (Math.random()*2+1.5)+'s';
      document.body.appendChild(c);
      setTimeout(() => c.remove(), 4000);
    }

    // ============ TAP INTERACTIONS ============
    function tapHeart(e) {
      const r = e.target.getBoundingClientRect();
      for(let i=0;i<10;i++) setTimeout(()=>createBurstHeart(r.left+r.width/2, r.top+r.height/2), i*40);
    }

    function tapPhotoFrame(e) {
      showModal('💑', 'Alam & Gulnaaz', 'Two hearts, one beautiful love story. Every chapter with you is my favorite.');
      const r = e.currentTarget.getBoundingClientRect();
      for(let i=0;i<8;i++) createBurstHeart(r.left+r.width/2, r.top+r.height/2);
    }

    function tapFinalHeart(e) {
      const r = e.target.getBoundingClientRect();
      for(let i=0;i<20;i++) setTimeout(()=>createBurstHeart(r.left+r.width/2, r.top+r.height/2), i*30);
      for(let i=0;i<40;i++) setTimeout(createConfetti, i*30);
    }

    // ============ REASONS INTERACTION ============
    function tapReason(card, e) {
      card.classList.add('tapped');
      const r = card.getBoundingClientRect();
      for(let i=0;i<5;i++) createBurstHeart(r.right-20, r.top+r.height/2);

      const messages = [
        '😊 Your smile is my sunshine!',
        '💪 You make me stronger every day!',
        '🥰 I could listen to you laugh forever!',
        '✨ You turn ordinary into extraordinary!',
        '🌍 My whole universe, right here!'
      ];
      const idx = [...card.parentElement.children].indexOf(card);
      if (messages[idx]) {
        showModal(['😊','💪','🥰','✨','🌍'][idx], 'You Are Special', messages[idx]);
      }
    }

    // ============ LOVE CALCULATOR ============
    let calcDone = false;
    function calculateLove() {
      if (calcDone) return;
      calcDone = true;
      document.getElementById('calcBtn').style.display = 'none';
      const result = document.getElementById('calcResult');
      result.classList.add('show');

      let current = 0;
      const target = 100;
      const percentEl = document.getElementById('calcPercent');
      const interval = setInterval(() => {
        current++;
        percentEl.textContent = current + '%';
        if (current >= target) {
          clearInterval(interval);
          percentEl.textContent = '💯 %';
          document.getElementById('calcMsg').classList.add('show');
          for(let i=0;i<25;i++) setTimeout(createConfetti, i*40);
        }
      }, 25);

      setTimeout(() => {
        document.getElementById('calcBar').style.width = '100%';
      }, 100);
    }

    // ============ PROMISES CAROUSEL ============
    let currentPromise = 0;
    const totalPromises = 5;

    function initPromises() {
      const dots = document.getElementById('promiseDots');
      for(let i=0;i<totalPromises;i++) {
        const dot = document.createElement('div');
        dot.classList.add('promise-dot');
        if(i===0) dot.classList.add('active');
        dot.onclick = () => goToPromise(i);
        dots.appendChild(dot);
      }
      updatePromiseCards();

      const carousel = document.getElementById('promiseCarousel');
      carousel.addEventListener('click', () => {
        goToPromise((currentPromise + 1) % totalPromises);
      });

      let touchStartX = 0;
      carousel.addEventListener('touchstart', e => { touchStartX = e.touches[0].clientX; }, {passive:true});
      carousel.addEventListener('touchend', e => {
        const diff = touchStartX - e.changedTouches[0].clientX;
        if(Math.abs(diff) > 40) {
          goToPromise(diff > 0 ? (currentPromise+1)%totalPromises : (currentPromise-1+totalPromises)%totalPromises);
        }
      }, {passive:true});
    }

    function goToPromise(idx) {
      currentPromise = idx;
      updatePromiseCards();
      document.querySelectorAll('.promise-dot').forEach((d,i) => d.classList.toggle('active', i===idx));
    }

    function updatePromiseCards() {
      document.querySelectorAll('.promise-card').forEach((card, i) => {
        card.className = 'promise-card';
        if(i === currentPromise) card.classList.add('active');
        else if(i === (currentPromise-1+totalPromises)%totalPromises) card.classList.add('prev');
        else if(i === (currentPromise+1)%totalPromises) card.classList.add('next');
      });
    }

    // ============ WISH JAR ============
    const wishes = [
      {emoji:'💌', text:'I wish for a lifetime of your hugs'},
      {emoji:'🌙', text:'I wish to see the stars with you every night'},
      {emoji:'🧁', text:'I wish to cook for you (& not burn it!)'},
      {emoji:'✈️', text:'I wish to travel the world with you'},
      {emoji:'🏡', text:'I wish for our own little home together'},
      {emoji:'💍', text:'I wish for forever with you, Gulnaaz'}
    ];

    function initWishJar() {
      const body = document.getElementById('jarBody');
      wishes.forEach((w, i) => {
        const note = document.createElement('div');
        note.classList.add('jar-note');
        note.textContent = w.emoji;
        note.style.left = (15 + Math.random()*70) + '%';
        note.style.top = (15 + Math.random()*55) + '%';
        note.style.animationDelay = (i*0.4) + 's';
        note.onclick = (e) => {
          e.stopPropagation();
          showModal(w.emoji, 'A Wish For Us', w.text);
          const r = note.getBoundingClientRect();
          for(let j=0;j<6;j++) createBurstHeart(r.left+r.width/2, r.top+r.height/2);
        };
        body.appendChild(note);
      });
    }

    // ============ SCRATCH CARD ============
    function initScratchCard() {
      const canvas = document.getElementById('scratchCanvas');
      const container = document.getElementById('scratchContainer');
      const rect = container.getBoundingClientRect();
      canvas.width = container.offsetWidth;
      canvas.height = container.offsetHeight;
      const ctx = canvas.getContext('2d');

      // Draw scratch overlay
      ctx.fillStyle = '#2d0a1e';
      ctx.fillRect(0, 0, canvas.width, canvas.height);

      // Decorative text on scratch surface
      ctx.fillStyle = '#ff6b9d';
      ctx.font = '16px Dancing Script, cursive';
      ctx.textAlign = 'center';
      ctx.fillText('Scratch Me!', canvas.width/2, canvas.height/2 - 10);
      ctx.font = '24px serif';
      ctx.fillText('🤫', canvas.width/2, canvas.height/2 + 25);

      // Draw sparkle dots
      for(let i=0;i<30;i++) {
        ctx.beginPath();
        ctx.arc(Math.random()*canvas.width, Math.random()*canvas.height, 1, 0, Math.PI*2);
        ctx.fillStyle = `rgba(255,107,157,${Math.random()*0.5})`;
        ctx.fill();
      }

      let isDrawing = false;
      let scratchedPixels = 0;
      const totalPixels = canvas.width * canvas.height;

      function scratch(x, y) {
        ctx.globalCompositeOperation = 'destination-out';
        ctx.beginPath();
        ctx.arc(x, y, 22, 0, Math.PI*2);
        ctx.fill();
        scratchedPixels += Math.PI * 22 * 22;
        if(scratchedPixels / totalPixels > 0.35) {
          canvas.style.transition = 'opacity 0.5s ease';
          canvas.style.opacity = '0';
          setTimeout(() => canvas.style.display = 'none', 500);
        }
      }

      canvas.addEventListener('mousedown', () => isDrawing = true);
      canvas.addEventListener('mouseup', () => isDrawing = false);
      canvas.addEventListener('mousemove', e => {
        if(!isDrawing) return;
        const r = canvas.getBoundingClientRect();
        scratch(e.clientX - r.left, e.clientY - r.top);
      });

      canvas.addEventListener('touchstart', e => { e.preventDefault(); isDrawing = true; }, {passive:false});
      canvas.addEventListener('touchend', () => isDrawing = false);
      canvas.addEventListener('touchmove', e => {
        e.preventDefault();
        const r = canvas.getBoundingClientRect();
        const t = e.touches[0];
        scratch(t.clientX - r.left, t.clientY - r.top);
      }, {passive:false});
    }

    // ============ SEND KISS / HUG ============
    function sendKiss(e) {
      const r = e.target.getBoundingClientRect();
      for(let i=0;i<15;i++) setTimeout(()=>createBurstHeart(r.left+r.width/2, r.top+r.height/2), i*50);
      for(let i=0;i<30;i++) setTimeout(createConfetti, i*40);
      showModal('💋', 'Kiss Sent!', 'A virtual kiss just flew to Gulnaaz!\nFilled with all the love in my heart.');
    }

    let hugCount = 0;
    function sendHug(e) {
      hugCount++;
      const counter = document.getElementById('hugCounter');
      counter.style.display = 'flex';
      document.getElementById('hugCountDisplay').textContent = hugCount;
      const r = e.target.getBoundingClientRect();
      for(let i=0;i<8;i++) setTimeout(()=>createBurstHeart(r.left+r.width/2, r.top+r.height/2), i*50);

      if(hugCount === 1) showModal('🤗', 'Hug Sent!', 'A warm hug just reached Gulnaaz!');
      else if(hugCount === 5) showModal('🥰', 'So Many Hugs!', '5 hugs! Gulnaaz must be feeling so loved!');
      else if(hugCount === 10) showModal('💕', 'Hug Champion!', '10 hugs! You really can\'t stop loving her, can you?');
      else if(hugCount % 10 === 0) showModal('🤗', hugCount + ' Hugs!', 'The hugs keep coming! Gulnaaz is the luckiest!');
    }

    // ============ MODAL ============
    function showModal(emoji, title, text) {
      document.getElementById('modalEmoji').textContent = emoji;
      document.getElementById('modalTitle').textContent = title;
      document.getElementById('modalText').textContent = text;
      document.getElementById('modalOverlay').classList.add('show');
    }

    function closeModal(e) {
      if(e && e.target !== document.getElementById('modalOverlay')) return;
      document.getElementById('modalOverlay').classList.remove('show');
    }

    // close on background click
    document.getElementById('modalOverlay').addEventListener('click', function(e) {
      if(e.target === this) this.classList.remove('show');
    });

    // ============ INTERSECTION OBSERVER ============
    function observeSections() {
      // Reasons cards stagger
      const reasonCards = document.querySelectorAll('.reason-card');
      const reasonObs = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if(entry.isIntersecting) {
            const cards = entry.target.querySelectorAll ? document.querySelectorAll('.reason-card') : [];
            reasonCards.forEach((card, i) => {
              setTimeout(() => card.classList.add('visible'), i * 150);
            });
          }
        });
      }, {threshold: 0.3});
      const reasonsSection = document.getElementById('sReasons');
      if(reasonsSection) reasonObs.observe(reasonsSection);

      // Timeline items stagger
      const timelineItems = document.querySelectorAll('.timeline-item');
      const timelineObs = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if(entry.isIntersecting) {
            timelineItems.forEach((item, i) => {
              setTimeout(() => item.classList.add('visible'), i * 300);
            });
          }
        });
      }, {threshold: 0.2});
      const timelineSection = document.getElementById('sTimeline');
      if(timelineSection) timelineObs.observe(timelineSection);

      // Love meter fill on final section
      const finalObs = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if(entry.isIntersecting) {
            setTimeout(() => {
              document.getElementById('meterFill').style.width = '100%';
            }, 500);
          }
        });
      }, {threshold: 0.3});
      const finalSection = document.getElementById('sFinal');
      if(finalSection) finalObs.observe(finalSection);

      // Hide scroll indicator on last section
      const lastObs = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          document.getElementById('scrollIndicator').style.opacity = entry.isIntersecting ? '0' : '1';
        });
      }, {threshold: 0.5});
      if(finalSection) lastObs.observe(finalSection);
    }

    // ============ TOUCH/MOUSE SPARKLE TRAIL ============
    document.addEventListener('touchmove', (e) => {
      const t = e.touches[0];
      const s = document.createElement('div');
      s.classList.add('sparkle');
      s.style.left = t.clientX+'px';
      s.style.top = t.clientY+'px';
      s.style.width = s.style.height = '6px';
      s.style.background = '#ff6b9d';
      s.style.animationDuration = '0.8s';
      document.body.appendChild(s);
      setTimeout(() => s.remove(), 800);
    }, {passive:true});

    document.addEventListener('mousemove', (e) => {
      if(Math.random()>0.85) {
        const s = document.createElement('div');
        s.classList.add('sparkle');
        s.style.left = e.clientX+'px';
        s.style.top = e.clientY+'px';
        s.style.width = s.style.height = '5px';
        s.style.background = '#ff6b9d';
        s.style.animationDuration = '0.8s';
        document.body.appendChild(s);
        setTimeout(() => s.remove(), 800);
      }
    });
  </script>
</body>
</html> -->
