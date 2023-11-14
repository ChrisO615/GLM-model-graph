# GLM-model-graph
nematode <- read.csv("nematode.csv")

unknown <- nematode$Unknown
Bacterivorous <- nematode$Bacterivorous
fungivorous <- nematode$Fungivorous
herbivorous <- nematode$Herbivorous
Predatory <- nematode$Predatory
Site <- nematode$Site

plot(nematode$Predatory, 
     breaks = 15,
     col = "purple", 
     xlab = "Site",
     ylab = "Frequency",
     main = "Predatory Nematodes per Site")

plot(nematode$Unknown, 
     breaks = 15,
     col = "maroon", 
     xlab = "Number of unknown Nematodes",
     ylab = "Frequency",
     main = "unknown Nematodes per Site")

plot(nematode$Bacterivorous, 
     breaks = 15,
     col = "navy", 
     xlab = "Site",
     ylab = "Frequency",
     main = "Bacterivorous Nematodes per Site")

plot(nematode$Fungivorous, 
     breaks = 15,
     col = "red", 
     xlab = "Site",
     ylab = "Frequency",
     main = "Fungivorous Nematodes per Site")

plot(nematode$Herbivorous, 
     breaks = 15,
     col = "blue", 
     xlab = "Site",
     ylab = "Frequency",
     main = "Herbivorous Nematodes per Site")





model <- glm(Total ~ Unknown + Bacterivorous + Fungivorous + Herbivorous + Omnivorous + Predatory, data = nematode, family = "poisson")
summary(model)

install.packages("visreg")
library(visreg)
model <- glm(Total ~ Unknown + Bacterivorous + Fungivorous + Herbivorous + Omnivorous + Predatory, data = nematode, family = "poisson")
visreg(model, scale = "response")
