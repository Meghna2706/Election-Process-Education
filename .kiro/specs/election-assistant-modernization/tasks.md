# Implementation Plan: Election Assistant Modernization

## Overview

This implementation plan breaks down the Election Assistant modernization into discrete, manageable coding tasks. Each task builds incrementally on previous steps, starting with the design system foundation, then creating reusable components, enhancing existing pages, and finally integrating everything together. The plan includes both core implementation tasks and optional testing tasks marked with `*`.

## Tasks

- [x] 1. Set up design system and core styling
  - [x] 1.1 Create design system tokens file
    - Create `src/styles/designSystem.ts` with all design tokens (colors, gradients, typography, spacing, shadows, border radius, transitions)
    - Export color palette (primary, secondary, accent, success, error, neutral shades)
    - Export gradient definitions for backgrounds and accents
    - Export typography scale (h1-h6, body, caption with sizes, weights, line heights)
    - Export spacing scale (8px-based: xs, sm, md, lg, xl, 2xl)
    - Export shadow definitions (sm, md, lg, xl)
    - Export border radius values (sm: 4px, md: 8px, lg: 12px, xl: 16px, 2xl: 24px)
    - Export transition timing values (fast: 200ms, normal: 300ms, slow: 500ms)
    - _Requirements: 1.1, 1.2, 1.3, 1.4, 1.5, 1.6, 1.7_

  - [x] 1.2 Update global styles
    - Update `src/styles/globals.css` with Tailwind configuration
    - Add custom color palette to Tailwind config
    - Add custom spacing scale to Tailwind config
    - Add custom shadow definitions to Tailwind config
    - Add custom border radius values to Tailwind config
    - Add custom transition timing to Tailwind config
    - Ensure Tailwind is properly configured in `tailwind.config.js`
    - _Requirements: 1.1, 1.2, 1.3, 1.4, 1.5, 1.6, 1.7_

  - [ ]* 1.3 Write property test for design system token consistency
    - **Property 1: Design System Token Consistency**
    - **Validates: Requirements 1.1, 1.2, 1.3, 1.4, 1.5, 1.6, 1.7, 1.8**
    - Create `src/styles/designSystem.test.ts`
    - Test that all design tokens are defined and exported
    - Test that color values are valid hex or rgb values
    - Test that spacing values follow 8px scale
    - Test that shadow definitions are valid CSS
    - _Requirements: 1.1, 1.2, 1.3, 1.4, 1.5, 1.6, 1.7_

- [x] 2. Create core reusable components
  - [x] 2.1 Create Button component
    - Create `src/components/common/Button.tsx`
    - Implement variants: primary, secondary, outline, ghost
    - Implement sizes: sm, md, lg
    - Implement states: default, hover, active, disabled, loading
    - Accept props: variant, size, disabled, loading, onClick, children, className
    - Use design system colors and transitions
    - _Requirements: 7.1, 1.8_

  - [ ]* 2.2 Write property test for Button component variants
    - **Property 25: Button Component Variants**
    - **Validates: Requirements 7.1**
    - Create `src/components/common/Button.test.tsx`
    - Test that all button variants render with correct styling
    - Test that button sizes apply correct padding and font sizes
    - Test that disabled state prevents click handlers
    - Test that loading state displays loading indicator
    - _Requirements: 7.1_

  - [x] 2.3 Create Card component
    - Create `src/components/common/Card.tsx`
    - Accept props: children, className, hover (boolean), gradient (boolean)
    - Implement rounded corners (2xl), soft shadow, padding
    - Implement hover effects with elevation change
    - Support gradient background variant
    - _Requirements: 7.2, 1.8_

  - [ ]* 2.4 Write property test for Card component consistency
    - **Property 26: Card Component Consistency**
    - **Validates: Requirements 7.2**
    - Create `src/components/common/Card.test.tsx`
    - Test that cards render with consistent styling
    - Test that hover prop applies hover effect classes
    - Test that gradient prop applies gradient background
    - Test that cards maintain padding and spacing consistency
    - _Requirements: 7.2_

  - [x] 2.5 Create Input component
    - Create `src/components/common/Input.tsx`
    - Accept props: type, placeholder, value, onChange, error, disabled, label, className
    - Implement states: default, focus, error, disabled
    - Display label above input field
    - Display error message below input when error prop is provided
    - Apply focus state styling (border color change)
    - _Requirements: 7.3, 1.8_

  - [ ]* 2.6 Write property test for Input component validation
    - **Property 27: Input Component Validation Support**
    - **Validates: Requirements 7.3**
    - Create `src/components/common/Input.test.tsx`
    - Test that input renders with label and placeholder
    - Test that error state displays error message
    - Test that onChange handler is called with correct value
    - Test that disabled state prevents input
    - _Requirements: 7.3_

  - [x] 2.7 Create Icon component
    - Create `src/components/common/Icon.tsx`
    - Accept props: name (lucide-react icon name), size, color, className
    - Integrate with lucide-react library
    - Support size variants (sm: 16px, md: 24px, lg: 32px)
    - Support color customization
    - _Requirements: 7.4, 11.1, 11.2, 11.3_

  - [ ]* 2.8 Write property test for Icon component lucide-react integration
    - **Property 28: Icon Component lucide-react Integration**
    - **Validates: Requirements 7.4**
    - Create `src/components/common/Icon.test.tsx`
    - Test that icons render using lucide-react
    - Test that icon sizes apply correct dimensions
    - Test that icon colors apply correct styling
    - Test that invalid icon names display placeholder
    - _Requirements: 7.4_

  - [x] 2.9 Create LoadingState component
    - Create `src/components/common/LoadingState.tsx`
    - Accept props: message, size
    - Display spinner animation with optional message
    - Use design system colors and animations
    - _Requirements: 8.1, 8.3_

  - [x] 2.10 Create EmptyState component
    - Create `src/components/common/EmptyState.tsx`
    - Accept props: icon, title, message, action (optional)
    - Display icon, title, message in centered layout
    - Display optional action button
    - Use design system colors
    - _Requirements: 8.2, 8.3, 8.5_

- [ ] 3. Create layout components
  - [x] 3.1 Create Navbar component
    - Create `src/components/layout/Navbar.tsx`
    - Display application logo/title
    - Display navigation links (Home, Chat, Eligibility, Timeline, Guide)
    - Implement responsive mobile menu (hamburger on mobile)
    - Use design system colors and spacing
    - _Requirements: 10.5, 1.8_

  - [ ] 3.2 Create Footer component
    - Create `src/components/layout/Footer.tsx`
    - Display footer content with links and information
    - Use design system colors and spacing
    - Implement responsive layout for mobile
    - _Requirements: 1.8_

  - [x] 3.3 Create Container component
    - Create `src/components/layout/Container.tsx`
    - Accept props: children, className
    - Provide consistent max-width and padding
    - Implement responsive breakpoints (mobile, tablet, desktop)
    - _Requirements: 10.1, 10.2, 10.3_

- [x] 4. Create feature components
  - [x] 4.1 Create HeroSection component
    - Create `src/components/features/HeroSection.tsx`
    - Accept props: title, subtitle, description, buttons, backgroundGradient
    - Display full-width section with gradient background
    - Center content with appropriate spacing
    - Implement responsive layout (stacks on mobile)
    - _Requirements: 2.1, 2.2, 1.8_

  - [ ]* 4.2 Write property test for HeroSection content presence
    - **Property 2: Hero Section Content Presence**
    - **Validates: Requirements 2.1**
    - Create `src/components/features/HeroSection.test.tsx`
    - Test that hero section renders headline, subheading, and CTA buttons
    - Test that gradient background classes are applied
    - Test that responsive classes are present for mobile/tablet/desktop
    - _Requirements: 2.1, 2.2_

  - [x] 4.3 Create FeatureCard component
    - Create `src/components/features/FeatureCard.tsx`
    - Accept props: icon, title, description, className
    - Display icon, title, description in card layout
    - Implement hover effect with elevation change
    - Use design system colors and spacing
    - _Requirements: 2.3, 2.4, 2.5, 1.8_

  - [ ]* 4.4 Write property test for FeatureCard hover effects
    - **Property 5: Feature Card Hover Effects**
    - **Validates: Requirements 2.5**
    - Create `src/components/features/FeatureCard.test.tsx`
    - Test that feature cards render with icon, title, description
    - Test that hover effect classes are applied
    - Test that cards maintain consistent styling
    - _Requirements: 2.5_

  - [x] 4.5 Create ChatMessage component
    - Create `src/components/features/ChatMessage.tsx`
    - Accept props: message, role (user/assistant), timestamp
    - Display user messages with different styling than assistant messages
    - Use different background colors for user vs. assistant
    - Display timestamp with message
    - _Requirements: 3.1, 3.2, 1.8_

  - [ ]* 4.6 Write property test for ChatMessage distinction
    - **Property 7: Chat Message Distinction**
    - **Validates: Requirements 3.1, 3.2**
    - Create `src/components/features/ChatMessage.test.tsx`
    - Test that user and assistant messages have distinct styling
    - Test that messages render with correct role-based background
    - Test that timestamps are displayed correctly
    - _Requirements: 3.1, 3.2_

  - [x] 4.7 Create TimelineEvent component
    - Create `src/components/features/TimelineEvent.tsx`
    - Accept props: date, title, description, icon, isLast
    - Display date, icon, title, description in card
    - Implement vertical connector line (except for last event)
    - Implement hover effect with elevation change
    - _Requirements: 5.1, 5.2, 5.3, 5.4, 5.5, 1.8_

  - [ ]* 4.8 Write property test for TimelineEvent styling
    - **Property 18: Timeline Event Styling**
    - **Validates: Requirements 5.4**
    - Create `src/components/features/TimelineEvent.test.tsx`
    - Test that timeline events render with date, title, description, icon
    - Test that connector lines are present (except last event)
    - Test that hover effect classes are applied
    - _Requirements: 5.4_

  - [x] 4.9 Create GuideStep component
    - Create `src/components/features/GuideStep.tsx`
    - Accept props: stepNumber, title, description, icon
    - Display numbered step badge with step number
    - Display icon, title, description
    - Implement distinct visual styling
    - Implement hover effect
    - _Requirements: 6.1, 6.2, 6.3, 6.4, 6.5, 1.8_

  - [ ]* 4.10 Write property test for GuideStep visual distinction
    - **Property 22: Guide Steps Visual Distinction**
    - **Validates: Requirements 6.3, 6.4**
    - Create `src/components/features/GuideStep.test.tsx`
    - Test that guide steps render with step number badge
    - Test that steps display icon, title, description
    - Test that hover effect classes are applied
    - _Requirements: 6.3, 6.4_

- [x] 5. Enhance Home page
  - [x] 5.1 Update Home page structure
    - Update `src/pages/Home.tsx` to use new components
    - Import HeroSection, FeatureCard, Container, Button components
    - Remove old styling and replace with new design system
    - _Requirements: 2.1, 2.2, 2.3, 2.4, 2.5, 2.6, 2.7_

  - [x] 5.2 Implement Home page HeroSection
    - Add HeroSection component with title, subtitle, description
    - Add call-to-action buttons (Get Started, Learn More)
    - Apply gradient background
    - Implement responsive layout
    - _Requirements: 2.1, 2.2, 2.6, 2.7_

  - [x] 5.3 Implement Home page feature cards
    - Add feature cards section with at least 3 feature cards
    - Each card displays icon, title, description
    - Cards have hover effects with elevation change
    - Implement responsive grid layout (1 column mobile, 3 columns desktop)
    - _Requirements: 2.3, 2.4, 2.5, 2.6, 2.7_

  - [ ]* 5.4 Write property test for Home page responsive layout
    - **Property 6: Home Page Responsive Classes**
    - **Validates: Requirements 2.6, 2.7**
    - Create `src/pages/Home.test.tsx`
    - Test that home page renders with responsive breakpoint classes
    - Test that hero section and feature cards are present
    - Test that layout adapts for mobile, tablet, desktop
    - _Requirements: 2.6, 2.7_

- [x] 6. Enhance Chat page
  - [x] 6.1 Update Chat page structure
    - Update `src/pages/Chat.tsx` to use new components
    - Import ChatMessage, LoadingState, EmptyState, Input, Container components
    - Remove old styling and replace with new design system
    - _Requirements: 3.1, 3.2, 3.3, 3.4, 3.5, 3.6, 3.7_

  - [x] 6.2 Implement Chat message display
    - Update message rendering to use ChatMessage component
    - Display user and assistant messages with distinct styling
    - Implement smooth scrolling to latest message
    - _Requirements: 3.1, 3.2, 3.6_

  - [x] 6.3 Implement Chat loading state
    - Add LoadingState component when messages are being generated
    - Display loading indicator with "Generating response..." message
    - _Requirements: 3.3_

  - [x] 6.4 Implement Chat empty state
    - Add EmptyState component when no messages exist
    - Display helpful guidance message
    - _Requirements: 3.4_

  - [x] 6.5 Implement Chat input field
    - Update input field to use Input component
    - Implement focus state with visual feedback
    - Display input field with placeholder text
    - _Requirements: 3.5_

  - [ ]* 6.6 Write property test for Chat message distinction
    - **Property 7: Chat Message Distinction**
    - **Validates: Requirements 3.1, 3.2**
    - Create `src/pages/Chat.test.tsx`
    - Test that chat messages render with distinct styling
    - Test that loading state displays when generating
    - Test that empty state displays when no messages
    - _Requirements: 3.1, 3.2, 3.3, 3.4_

  - [ ]* 6.7 Write property test for Chat page responsive layout
    - **Property 11: Chat Page Responsive Layout**
    - **Validates: Requirements 3.6, 3.7**
    - Test that chat page includes responsive breakpoint classes
    - Test that layout adapts for mobile, tablet, desktop
    - _Requirements: 3.6, 3.7_

- [x] 7. Enhance Eligibility page
  - [x] 7.1 Update Eligibility page structure
    - Update `src/pages/Eligibility.tsx` to use new components
    - Import Input, Button, Card, Container components
    - Remove old styling and replace with new design system
    - _Requirements: 4.1, 4.2, 4.3, 4.4, 4.5, 4.6, 4.7_

  - [x] 7.2 Implement Eligibility form fields
    - Update form fields to use Input component
    - Add labels and placeholders to all fields
    - Implement focus states with visual feedback
    - _Requirements: 4.1, 4.2_

  - [x] 7.3 Implement Eligibility form validation
    - Add error message display for invalid fields
    - Display error state styling on invalid fields
    - _Requirements: 4.2, 4.3_

  - [x] 7.4 Implement Eligibility result display
    - Create result card with eligibility status
    - Use color coding (green for eligible, red for ineligible)
    - Display supporting icons and messages
    - _Requirements: 4.4, 4.5_

  - [ ]* 7.5 Write property test for Eligibility form validation
    - **Property 13: Form Field Validation Feedback**
    - **Validates: Requirements 4.2, 4.3**
    - Create `src/pages/Eligibility.test.tsx`
    - Test that form fields display error messages on validation failure
    - Test that error state styling is applied
    - Test that result card displays with correct status
    - _Requirements: 4.2, 4.3, 4.4, 4.5_

  - [ ]* 7.6 Write property test for Eligibility page responsive layout
    - **Property 15: Eligibility Page Responsive Layout**
    - **Validates: Requirements 4.6, 4.7**
    - Test that eligibility page includes responsive breakpoint classes
    - Test that form layout adapts for mobile, tablet, desktop
    - _Requirements: 4.6, 4.7_

- [x] 8. Create Timeline page
  - [x] 8.1 Create Timeline page component
    - Create `src/pages/Timeline.tsx`
    - Import TimelineEvent, Container, EmptyState components
    - Implement page structure with title and description
    - _Requirements: 5.1, 5.2, 5.3, 5.4, 5.5, 5.6, 5.7_

  - [x] 8.2 Implement Timeline events rendering
    - Fetch or define timeline events data
    - Render each event using TimelineEvent component
    - Display events in vertical list with connector lines
    - _Requirements: 5.1, 5.2, 5.3, 5.4_

  - [x] 8.3 Implement Timeline hover effects
    - Ensure TimelineEvent components have hover effects
    - Display elevation change on hover
    - _Requirements: 5.5_

  - [x] 8.4 Implement Timeline responsive layout
    - Add responsive breakpoint classes for mobile, tablet, desktop
    - Adjust spacing and layout for different screen sizes
    - _Requirements: 5.6, 5.7_

  - [ ]* 8.5 Write property test for Timeline events rendering
    - **Property 16: Timeline Events Rendering**
    - **Validates: Requirements 5.1, 5.2**
    - Create `src/pages/Timeline.test.tsx`
    - Test that timeline renders events with dates, titles, descriptions, icons
    - Test that connector lines are present between events
    - Test that responsive classes are applied
    - _Requirements: 5.1, 5.2, 5.3_

  - [ ]* 8.6 Write property test for Timeline page responsive layout
    - **Property 20: Timeline Page Responsive Layout**
    - **Validates: Requirements 5.6, 5.7**
    - Test that timeline page includes responsive breakpoint classes
    - Test that layout adapts for mobile, tablet, desktop
    - _Requirements: 5.6, 5.7_

- [x] 9. Create Guide page
  - [x] 9.1 Create Guide page component
    - Create `src/pages/Guide.tsx`
    - Import GuideStep, Container, EmptyState components
    - Implement page structure with title and description
    - _Requirements: 6.1, 6.2, 6.3, 6.4, 6.5, 6.6, 6.7_

  - [x] 9.2 Implement Guide steps rendering
    - Fetch or define guide steps data
    - Render each step using GuideStep component
    - Display steps in logical order with clear visual hierarchy
    - _Requirements: 6.1, 6.2, 6.3, 6.4_

  - [x] 9.3 Implement Guide hover effects
    - Ensure GuideStep components have hover effects
    - Display smooth hover effect on step cards
    - _Requirements: 6.5_

  - [x] 9.4 Implement Guide responsive layout
    - Add responsive breakpoint classes for mobile, tablet, desktop
    - Adjust spacing and layout for different screen sizes
    - _Requirements: 6.6, 6.7_

  - [ ]* 9.5 Write property test for Guide steps rendering
    - **Property 21: Guide Steps Rendering**
    - **Validates: Requirements 6.1, 6.2**
    - Create `src/pages/Guide.test.tsx`
    - Test that guide renders numbered steps with titles, descriptions, icons
    - Test that steps display in logical order
    - Test that responsive classes are applied
    - _Requirements: 6.1, 6.2, 6.3, 6.4_

  - [ ]* 9.6 Write property test for Guide page responsive layout
    - **Property 24: Guide Page Responsive Layout**
    - **Validates: Requirements 6.6, 6.7**
    - Test that guide page includes responsive breakpoint classes
    - Test that layout adapts for mobile, tablet, desktop
    - _Requirements: 6.6, 6.7_

- [x] 10. Implement animations and transitions
  - [x] 10.1 Add page load fade-in animations
    - Add fade-in animation classes to all page components
    - Use design system transition timing (300ms)
    - _Requirements: 9.1_

  - [x] 10.2 Add interactive element hover effects
    - Ensure all interactive elements (buttons, cards, links) have hover effects
    - Use smooth transitions with design system timing
    - _Requirements: 9.2_

  - [x] 10.3 Add modal/overlay fade-in animations
    - Add fade-in animation classes to modals and overlays
    - Use design system transition timing
    - _Requirements: 9.3_

  - [x] 10.4 Add content change transitions
    - Implement transitions for content changes (fade, slide, scale)
    - Use design system transition timing
    - _Requirements: 9.4, 9.5_

  - [ ]* 10.5 Write property test for animation timing consistency
    - **Property 41: Animation Timing Consistency**
    - **Validates: Requirements 9.5**
    - Create `src/styles/animations.test.ts`
    - Test that all animations use consistent timing values (200ms, 300ms, 500ms)
    - Test that animation classes are applied correctly
    - _Requirements: 9.5_

- [x] 11. Implement responsive design
  - [x] 11.1 Add mobile responsive classes
    - Add sm: breakpoint classes for mobile layouts (< 768px)
    - Adjust typography, spacing, and layout for mobile
    - _Requirements: 10.1_

  - [x] 11.2 Add tablet responsive classes
    - Add md: breakpoint classes for tablet layouts (768px - 1024px)
    - Adjust typography, spacing, and layout for tablet
    - _Requirements: 10.2_

  - [x] 11.3 Add desktop responsive classes
    - Add lg: breakpoint classes for desktop layouts (> 1024px)
    - Display full-width content with appropriate spacing
    - _Requirements: 10.3_

  - [x] 11.4 Ensure touch target sizing
    - Verify all interactive elements have minimum 44px touch target
    - Add size classes to buttons, inputs, links
    - _Requirements: 10.4_

  - [x] 11.5 Ensure mobile navigation accessibility
    - Verify navigation is accessible on mobile
    - Ensure hamburger menu is properly sized and labeled
    - _Requirements: 10.5_

  - [x] 11.6 Ensure mobile typography readability
    - Verify typography is readable on mobile
    - Add appropriate sizing classes for mobile
    - _Requirements: 10.6_

  - [ ]* 11.7 Write property test for responsive layout
    - **Property 42: Mobile Responsive Layout**
    - **Validates: Requirements 10.1**
    - Create `src/components/layout/Container.test.tsx`
    - Test that container applies responsive breakpoint classes
    - Test that layout adapts for mobile, tablet, desktop
    - _Requirements: 10.1, 10.2, 10.3_

- [x] 12. Verify existing functionality
  - [x] 12.1 Test existing routes
    - Verify Home, Chat, Eligibility routes render without errors
    - Verify all existing pages display expected content
    - _Requirements: 12.1_

  - [x] 12.2 Test navigation between routes
    - Verify navigation links work correctly
    - Verify page transitions are smooth
    - _Requirements: 12.2_

  - [x] 12.3 Test chat functionality
    - Verify chat messages send and receive correctly
    - Verify chat interface displays messages properly
    - _Requirements: 12.3_

  - [x] 12.4 Test form submission
    - Verify eligibility form submits successfully
    - Verify form data is processed correctly
    - _Requirements: 12.4_

  - [ ]* 12.5 Write property test for existing routes functionality
    - **Property 51: Existing Routes Functionality**
    - **Validates: Requirements 12.1**
    - Create `src/pages/__tests__/routes.test.tsx`
    - Test that all existing routes render without errors
    - Test that routes display expected content
    - _Requirements: 12.1_

  - [ ]* 12.6 Write property test for form submission preservation
    - **Property 54: Form Submission Preservation**
    - **Validates: Requirements 12.4**
    - Test that eligibility form submits successfully
    - Test that form data is processed correctly
    - _Requirements: 12.4_

- [ ] 13. Checkpoint - Ensure all tests pass
  - Ensure all unit tests pass
  - Ensure all property-based tests pass
  - Verify no console errors or warnings
  - Ask the user if questions arise

- [x] 14. Final integration and verification
  - [x] 14.1 Verify design system consistency
    - Audit all components to ensure they use design system tokens
    - Verify no hardcoded colors or spacing values
    - _Requirements: 1.8_

  - [x] 14.2 Verify component library organization
    - Verify all components are in correct directories
    - Verify components are properly exported
    - _Requirements: 7.7_

  - [x] 14.3 Verify responsive design
    - Test application on mobile, tablet, desktop viewports
    - Verify layouts adapt correctly
    - _Requirements: 10.1, 10.2, 10.3_

  - [x] 14.4 Verify animations and transitions
    - Test all animations and transitions work smoothly
    - Verify animation timing is consistent
    - _Requirements: 9.1, 9.2, 9.3, 9.4, 9.5_

  - [x] 14.5 Verify icon integration
    - Verify all icons render correctly using lucide-react
    - Verify icon sizes and colors are consistent
    - _Requirements: 11.1, 11.2, 11.3_

  - [x] 14.6 Verify build process
    - Run build command and verify no errors
    - Verify application builds successfully
    - _Requirements: 12.5_

- [ ] 15. Final checkpoint - Ensure all tests pass
  - Ensure all unit tests pass
  - Ensure all property-based tests pass
  - Verify no console errors or warnings
  - Verify application builds successfully
  - Ask the user if questions arise

## Notes

- Tasks marked with `*` are optional testing tasks and can be skipped for faster MVP
- Each task references specific requirements for traceability
- Checkpoints ensure incremental validation
- Property-based tests validate universal correctness properties
- Unit tests validate specific examples and edge cases
- Core implementation tasks (without `*`) should be completed for full feature coverage
- Optional testing tasks can be added later for comprehensive test coverage
